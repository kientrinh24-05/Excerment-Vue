<template>
  <div>
    <base-header class="pb-6 pb-8 pt-5 pt-md-8 bg-gradient-success">
      <!-- Card stats -->
    </base-header>
    <b-container fluid class="mt--7">
      <b-row>
        <b-col>
          <div class="items-click-add">
            <h3>Danh sách nguyên liệu</h3>
            <div>
              <b-button v-b-modal.modal-1>Tạo nguyên liệu</b-button>

              <b-modal id="modal-1" title="BootstrapVue">
                <p class="my-4">Thêm nguyên liệu</p>
                <div>
                  <b-form @submit="onSubmit" @reset="onReset" v-if="show">
                    <b-form-group
                      id="input-group-1"
                      label="Tên nguyên liệu"
                      label-for="input-1"
                      description="We'll never share your email with anyone else."
                    >
                      <b-form-input
                        id="input-1"
                        v-model="form.email"
                        type="email"
                        placeholder="Nhập tên nguyên liệu"
                        required
                      ></b-form-input>
                    </b-form-group>

                    <b-form-group
                      id="input-group-2"
                      label="Nhà Phân Phối"
                      label-for="input-2"
                    >
                      <b-form-input
                        id="input-2"
                        v-model="form.name"
                        placeholder="Nhập nhà phân phối"
                        required
                      ></b-form-input>
                    </b-form-group>

                    <b-form-group id="input-group-3" label="Số Lượng" label-for="input-3">
                      <b-form-input
                        id="input-3"
                        v-model="form.name"
                        placeholder="Nhập số lượng"
                        required
                      ></b-form-input>
                    </b-form-group>
                    <b-form-group
                      id="input-group-2"
                      label="Ngày nhập"
                      label-for="input-2"
                    >
                      <div class="">
                        <input
                          class="form-control"
                          type="datetime-local"
                          value="2011-08-19T13:45:00"
                          id="example-datetime-local-input"
                        />
                      </div>
                    </b-form-group>

                    <b-button type="submit" variant="primary">Submit</b-button>
                    <b-button type="reset" variant="danger">Reset</b-button>
                  </b-form>
                </div>
              </b-modal>
            </div>
          </div>

          <light-table />
        </b-col>
      </b-row>
      <div class="mt-5"></div>
    </b-container>
  </div>
</template>
<script>
import { Dropdown, DropdownItem, DropdownMenu, Table, TableColumn } from "element-ui";
import projects from "./Tables/projects";
import users from "./Tables/users";
import LightTable from "./Tables/RegularTables/LightTable";

export default {
  components: {
    LightTable,
    [Dropdown.name]: Dropdown,
    [DropdownItem.name]: DropdownItem,
    [DropdownMenu.name]: DropdownMenu,
    [Table.name]: Table,
    [TableColumn.name]: TableColumn,
  },
  data() {
    return {
      projects,
      users,
      form: {
        email: "",
        name: "",
        food: null,
        checked: [],
      },
      show: true,
    };
  },
  methods: {
    onSubmit(event) {
      event.preventDefault();
      alert(JSON.stringify(this.form));
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
<style>
.el-table.table-dark {
  background-color: #172b4d;
  color: #f8f9fe;
}

.el-table.table-dark th,
.el-table.table-dark tr {
  background-color: #172b4d;
}

.el-table.table-dark td,
.el-table.table-dark th.is-leaf {
  border-bottom: none;
}
.items-click-add {
  margin: 1rem 0;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
