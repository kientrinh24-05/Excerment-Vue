<template>
  <div>
    <!-- BootstrapVue Done -->
    <base-header class="pb-6 pb-8 pt-5 pt-md-8 bg-gradient-success">
      <!-- Card stats -->
      <b-row>
        <b-col xl="3" md="6">
          <stats-card
            title="Tổng số bàn"
            type="gradient-red"
            sub-title="350,897"
            class="mb-4"
          >
          </stats-card>
        </b-col>
        <b-col xl="3" md="6">
          <stats-card
            title="Bàn Trống"
            type="gradient-orange"
            sub-title="2,356"
            class="mb-4"
          >
          </stats-card>
        </b-col>
        <b-col xl="3" md="6">
          <stats-card
            title="Bàn Đã Có Người"
            type="gradient-green"
            sub-title="924"
            class="mb-4"
          >
          </stats-card>
        </b-col>

        <b-col xl="3" md="6">
          <stats-card>
            <div>
              <!-- Using modifiers -->

              <!-- Using value -->

              <b-button v-b-modal="'my-modal'">Tạo bàn</b-button>
              <b-button>Chuyển bàn</b-button>

              <!-- The modal -->
              <b-modal id="my-modal">
                <form action="">
                  <label class="" style="display: flex" for="">Mã bàn ăn</label>
                  <input type="text" placeholder="Nhập mã bàn ăn" style="width: 100%" />
                  <hr />
                  <div>
                    <b-dropdown split split-href="#foo/bar" text="Trạng Thái" class="m-2">
                      <b-dropdown-item href="#">Có người</b-dropdown-item>
                      <b-dropdown-item href="#">Trống</b-dropdown-item>
                      <b-dropdown-item href="#">Tạm ngưng hoạt động</b-dropdown-item>
                    </b-dropdown>
                  </div>
                </form>
              </b-modal>
            </div>
          </stats-card>
        </b-col>
      </b-row>
    </base-header>

    <b-container fluid class="mt--7">
      <b-row class="justify-content-center">
        <b-col lg="12">
          <card header-classes="bg-transparent">
            <h3 slot="header" class="mb-0">Tất cả bàn ăn</h3>
            <b-row class="icon-examples">
              <b-col lg="3" md="6">
                <b-button v-b-modal.modal-1 class="btn-icon-clipboard sucses"
                  >101
                  <div>
                    <b-modal id="modal-1" title="BootstrapVue">
                      <p class="my-4">Bàn 1</p>
                    </b-modal>
                  </div>
                </b-button>
              </b-col>
              <b-col lg="3" md="6">
                <b-button  v-b-modal.modal-2 class="btn-icon-clipboard no-sucses">102
                  <b-modal id="modal-2" title="BootstrapVue">
                      <p class="my-4">Bàn 2</p>
                    </b-modal>
                </b-button>
              </b-col>
              <b-col lg="3" md="6">
                <b-button class="btn-icon-clipboard no-sucses">103</b-button>
              </b-col>
              <b-col lg="3" md="6">
                <b-button class="btn-icon-clipboard sucses">104</b-button>
              </b-col>
              <b-col lg="3" md="6">
                <b-button class="btn-icon-clipboard sucses">105</b-button>
              </b-col>
              <b-col lg="3" md="6">
                <b-button class="btn-icon-clipboard no-sucses">106</b-button>
              </b-col>
              <b-col lg="3" md="6">
                <b-button class="btn-icon-clipboard no-sucses">107</b-button>
              </b-col>
              <b-col lg="3" md="6">
                <b-button class="btn-icon-clipboard change">108</b-button>
              </b-col>
              <b-col lg="3" md="6">
                <b-button class="btn-icon-clipboard change">109</b-button>
              </b-col>
              <b-col lg="3" md="6">
                <b-button class="btn-icon-clipboard change">110</b-button>
              </b-col>
              <b-col lg="3" md="6">
                <b-button class="btn-icon-clipboard change">111</b-button>
              </b-col>
              <b-col lg="3" md="6">
                <b-button class="btn-icon-clipboard change">112</b-button>
              </b-col>
            </b-row>
          </card>
        </b-col>

        <div>
          <ul>
            <li>
              <div class="bg-span sucses"></div>
              Đã có người
            </li>
            <li>
              <div class="bg-span no-sucses"></div>
              Bàn Trống
            </li>
            <li>
              <div class="bg-span change"></div>
              Tạm ngưng hoạt động
            </li>
          </ul>
        </div>
      </b-row>
    </b-container>
  </div>
</template>
<script>
import Vue from "vue";
import VueClipboard from "vue-clipboard2";
import BaseHeader from "@/components/BaseHeader";

Vue.use(VueClipboard);
export default {
  name: "icons",
  components: {
    BaseHeader,
  },
  methods: {
    onCopy() {
      this.$notify({
        type: "info",
        message: "Copied to clipboard",
      });
    },
  },
};
</script>
<style>
ul {
  list-style: none;
  display: flex;
}
ul li {
  margin-right: 2rem;
}
.bg-span {
  width: 14px;
  height: 15px;
  background: red;
}
.btn-icon-clipboard {
  height: 5rem;
  border: 1px solid gray;
  text-align: center;
  font-weight: bold;
}
.sucses {
  background: red;
}
.no-sucses {
  background: green;
}
.change {
  background: yellow;
}
</style>
