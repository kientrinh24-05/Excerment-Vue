<template>
  <div>
    <b-card no-body>
      <div>
        <b-table class="table-sc" striped hover :items="items" :fields="fields">
          <template #cell(actions)="row">
            <i
              @click="info(row.item, row.index, $event.target)"
              class="fas fa-pencil-alt"
            ></i>
          </template>
        </b-table>

        <!-- Modal  -->
        <b-modal :id="infoModal.id" :title="infoModal.title" ok-only>
          <pre></pre>
          <div>
            <h2 style="text-align: center">Sửa Món Ăn</h2>
            <div>
              <b-form @submit="onSubmit" @reset="onReset" v-if="show">
                <b-form-group id="input-group-1" label="Tên Sản Phẩm" label-for="input-1">
                  <b-form-input
                    id="input-1"
                    v-model="form.email"
                    type="text"
                    placeholder="Tên Sản Phẩm"
                    required
                  ></b-form-input>
                </b-form-group>

                <b-form-group
                  id="input-group-2"
                  label="Giá Sản Phẩm:"
                  label-for="input-2"
                >
                  <b-form-input
                    id="input-2"
                    v-model="form.name"
                    placeholder="Giá Sản Phẩm"
                    required
                  ></b-form-input>
                </b-form-group>

                <div class="item-group">
                  <b-form-group id="input-group-2" label-for="input-2">
                    <b-dropdown
                      text="Loại s.phẩm"
                      block
                      variant="primary"
                      class="m-2"
                      menu-class="w-100"
                    >
                      <b-dropdown-item href="#">Tất cả</b-dropdown-item>
                      <b-dropdown-item href="#">Gạo</b-dropdown-item>
                      <b-dropdown-item href="#">Trái cây</b-dropdown-item>
                      <b-dropdown-item href="#">Ăn nhanh</b-dropdown-item>
                    </b-dropdown>
                  </b-form-group>

                  <!-- Status Product -->
                  <b-form-group id="input-group-2" label="" label-for="input-2">
                    <b-dropdown
                      text="Trạng thái"
                      block
                      variant="primary"
                      class="m-2"
                      menu-class="w-100"
                    >
                      <b-dropdown-item href="#">Còn</b-dropdown-item>
                      <b-dropdown-item href="#">Hết</b-dropdown-item>
                    </b-dropdown>
                  </b-form-group>

                  <b-form-group>
                  

                    <div>
                      <!-- Using modifiers -->
            
                      <b-button v-b-modal.modal-lg variant="primary">Xem Ng.Liệu</b-button>


                      <!-- The modal -->
                      <b-modal id="modal-lg" size="lg" >Danh sách nguyên liệu được dùng</b-modal>
                    </div>
                  </b-form-group>
                </div>

                <!-- Show Modal Nguyên Liệu -->

                <!-- Button Click Submit -->
                <div class="link-btn">
                  <b-button type="submit" variant="primary">Submit</b-button>
                  <b-button type="reset" variant="danger">Reset</b-button>
                </div>
              </b-form>
            </div>
          </div>
        </b-modal>
      </div>

      <b-card-footer class="py-4 d-flex justify-content-end">
        <base-pagination
          v-model="currentPage"
          :per-page="10"
          :total="40"
        ></base-pagination>
      </b-card-footer>
    </b-card>
    <!-- End -->
  </div>

  <!-- Info modal -->
</template>
<script>
import projects from "./../projects";
import { Table, TableColumn } from "element-ui";
import DarkTable from "./DarkTable.vue";
export default {
  name: "light-table",
  components: {
    [Table.name]: Table,
    [TableColumn.name]: TableColumn,
    DarkTable,
  },
  data() {
    return {
      projects,
      currentPage: 1,
      infoModal: {
        id: "info-modal",
        title: "",
        content: "",
      },
      fields: [
        {
          key: "id_product",
          sortable: true,
        },
        {
          key: "name_product",
          sortable: false,
        },
        {
          key: "species_product",

          sortable: true,
          // Variant applies to the whole column, including the header and footer
        },
        {
          key: "price_product",

          sortable: true,
          // Variant applies to the whole column, including the header and footer
        },
        {
          key: "status",

          sortable: true,
          // Variant applies to the whole column, including the header and footer
        },

        { key: "actions", label: "Actions" },
      ],
      items: [
        {
          isActive: true,
          id_product: 1,
          name_product: "Gạo Tẻ",
          species_product: "Gạo",
          price_product: "200000",
          status: "Còn",
        },
        {
          isActive: true,
          id_product: 2,
          name_product: "Nước Suối",
          species_product: "Nước",
          price_product: "100000",
          status: "Hết",
        },
        {
          isActive: true,
          id_product: 3,
          name_product: "Cam Sành",
          species_product: "Trái Cây",
          price_product: "1122",
          status: "Còn",
        },
      ],
      form: {
        email: "",
        name: "",
        food: null,
        checked: [],
      },
      show: true,
    };
  },
  computed: {
    sortOptions() {
      // Create an options list from our fields
      return this.fields
        .filter((f) => f.sortable)
        .map((f) => {
          return { text: f.label, value: f.key };
        });
    },
  },
  mounted() {
    // Set the initial number of items
    this.totalRows = this.items.length;
  },
  methods: {
    info(item, index, button) {
      this.infoModal.title = `Row index: ${index}`;
      this.infoModal.content = JSON.stringify(item, null, 2);
      this.$root.$emit("bv::show::modal", this.infoModal.id, button);
    },
    resetInfoModal() {
      this.infoModal.title = "";
      this.infoModal.content = "";
    },
    onFiltered(filteredItems) {
      // Trigger pagination to update the number of buttons/pages due to filtering
      this.totalRows = filteredItems.length;
      this.currentPage = 1;
    },
    onSubmit(event) {
      event.preventDefault();
      // alert(JSON.stringify(this.form));
    },
    onReset(event) {
      event.preventDefault();
      // Reset our form values
      this.form.email = "";
      this.form.name = "";
      this.form.food = null;
      this.form.checked = [];
      // Trick to reset/clear native browser form validation state
      this.show = false;
      this.$nextTick(() => {
        this.show = true;
      });
    },
  },
};
</script>
<style scoped>
.table-sc {
  text-align: center;
}
.fa-pencil-alt {
  font-size: 1rem;
  font-weight: bold;
  cursor: pointer;
}
.item-group {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.link-btn {
  text-align: center;
}
.modal-content  {
width: 120% !important;}
</style>
