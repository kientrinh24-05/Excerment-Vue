<template>
  <div>
    <base-header class="pb-6 pb-8 pt-5 pt-md-8 bg-gradient-success">
      <!-- Card stats -->
    </base-header>
    <b-container fluid class="mt--7">
      <b-row>
        <div>
          <b-card no-body>
            <b-tabs pills card >
              <b-tab title="Tất cả" active 
                ><b-card-text>
                  <div>
                    <b-card-group deck>
                      <b-card
                        img-src="https://picsum.photos/600/300/?image=25"
                        img-alt="Image"
                        img-top
                        tag="article"
                        style="max-width: 10rem"
                        class="mb-2"
                      >
                        <b class="price">2.000.000đ</b>
                        <p>Trà Tắc Xí Muội</p>
                      </b-card>
                       <b-card
                        img-src="https://picsum.photos/600/300/?image=25"
                        img-alt="Image"
                        img-top
                        tag="article"
                        style="max-width: 10rem"
                        class="mb-2"
                      >
                        <b class="price">2.000.000đ</b>
                        <p>Trà Tắc Xí Muội</p>
                      </b-card>
                      

                      <b-card
                        img-src="https://picsum.photos/600/300/?image=25"
                        img-alt="Image"
                        img-top
                        tag="article"
                        style="max-width: 10rem"
                        class="mb-2"
                      >
                        <b class="price">2.000.000đ</b>
                        <p>Trà Tắc Xí Muội</p>
                      </b-card>

                      <b-card
                        img-src="https://picsum.photos/600/300/?image=25"
                        img-alt="Image"
                        img-top
                        tag="article"
                        style="max-width: 10rem"
                        class="mb-2"
                      >
                        <b class="price">2.000.000đ</b>
                        <p>Trà Tắc Xí Muội</p>
                      </b-card>
                      <b-card
                        img-src="https://picsum.photos/600/300/?image=25"
                        img-alt="Image"
                        img-top
                        tag="article"
                        style="max-width: 10rem"
                        class="mb-2"
                      >
                        <b class="price">2.000.000đ</b>
                        <p>Trà Tắc Xí Muội</p>
                      </b-card>
                    </b-card-group>
                  </div>
                </b-card-text></b-tab
              >
              <b-tab title="Gạo"
                ><b-card-text>
                  <div>
                    <b-card-group deck>
                      <b-card
                        img-src="https://picsum.photos/600/300/?image=25"
                        img-alt="Image"
                        img-top
                        tag="article"
                        style="max-width: 10rem"
                        class="mb-2"
                      >
                        <b class="price">2.000.000đ</b>
                        <p>Trà Tắc Xí Muội</p>
                      </b-card>
                      <b-card
                        img-src="https://picsum.photos/600/300/?image=25"
                        img-alt="Image"
                        img-top
                        tag="article"
                        style="max-width: 10rem"
                        class="mb-2"
                      >
                        <b class="price">2.000.000đ</b>
                        <p>Trà Tắc Xí Muội</p>
                      </b-card>
                    </b-card-group>
                  </div>
                </b-card-text>
              </b-tab>
              <b-tab title="Trái cây"
                ><b-card-text>
                  <div>
                    <b-card-group deck>
                      <b-card
                        img-src="https://picsum.photos/600/300/?image=25"
                        img-alt="Image"
                        img-top
                        tag="article"
                        style="max-width: 10rem"
                        class="mb-2"
                      >
                        <b class="price">2.000.000đ</b>
                        <p>Trà Tắc Xí Muội</p>
                      </b-card>
                      <b-card
                        img-src="https://picsum.photos/600/300/?image=25"
                        img-alt="Image"
                        img-top
                        tag="article"
                        style="max-width: 10rem"
                        class="mb-2"
                      >
                        <b class="price">2.000.000đ</b>
                        <p>Trà Tắc Xí Muội</p>
                      </b-card>
                    </b-card-group>
                  </div>
                </b-card-text></b-tab
              >
              <b-tab title="Ăn nhanh"
                ><b-card-text>
                  <div>
                    <b-card-group deck>
                      <b-card no
                        img-src="https://picsum.photos/600/300/?image=25"
                        img-alt="Image"
                        img-top
                        tag="article"
                        style="max-width: 10rem"
                        class="mb-2"
                      >
                        <b class="price">2.000.000đ</b>
                        <p>Trà Tắc Xí Muội</p>
                      </b-card>
                      <b-card
                        img-src="https://picsum.photos/600/300/?image=25"
                        img-alt="Image"
                        img-top
                        tag="article"
                        style="max-width: 10rem"
                        class="mb-2"
                      >
                        <b class="price">2.000.000đ</b>
                        <p>Trà Tắc Xí Muội</p>
                      </b-card>
                    </b-card-group>
                  </div></b-card-text
                ></b-tab
              >
            </b-tabs>
          </b-card>
        </div>
        <!-- <b-col>
          <h3>Danh sách món ăn</h3>
          <light-table />
        </b-col> -->
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
    };
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
</style>
