<template>
  <div class="admin container body-view">
    <form
      method="POST"
      action="/admin/handle-form"
      class="col-12 container-form"
    >
      <h2 class="admin-header_text">Danh sách thức uống có trong Menu</h2>
      <div class="d-flex changs-page">
        <a href="/admin" class="btn btn-success mr-4 my-4">Quay lại</a>
      </div>

      <table class="table table-hover table-dark col-sm-12">
        <thead>
          <tr>
            <th scope="col">Cafe</th>
            <th scope="col">Tên thức uống</th>
            <th scope="col">Giá</th>
            <th scope="col" class="text-center">Tùy chọn</th>
          </tr>
        </thead>

        <tbody v-for="cafe in cafes" :key="cafe.id">
          <tr>
            <th scope="row">
              {{ cafe._id }}
            </th>
            <td>{{ cafe.name }}</td>
            <td>{{ cafe.price }}</td>
            <td>
              <p @click="restore(cafe._id)" class="btn btn-link btn-restore">
                Khôi phục
              </p>
              <button
                type="button"
                class="btn btn-primary"
                data-toggle="modal"
                data-target="#exampleModal"
                @click="this.id = cafe._id"
              >
                Xóa vĩnh viễn
              </button>
            </td>
          </tr>
        </tbody>
      </table>
      <table class="table table-hover table-dark">
        <thead>
          <tr>
            <th scope="col">Phindi</th>
            <th scope="col">Tên thức uống</th>
            <th scope="col">Giá</th>
            <th scope="col" class="text-center">Tùy chọn</th>
          </tr>
        </thead>
        <tbody v-for="phindi in phindis" :key="phindi.id">
          <tr>
            <th scope="row">
              {{ phindi._id }}
            </th>
            <td>{{ phindi.name }}</td>
            <td>{{ phindi.price }}</td>
            <td>
              <p @click="restore(phindi._id)" class="btn btn-link btn-restore">
                Khôi phục
              </p>
              <button
                type="button"
                class="btn btn-primary"
                data-toggle="modal"
                data-target="#exampleModal"
                @click="this.id = phindi._id"
              >
                Xóa vĩnh viễn
              </button>
            </td>
          </tr>
        </tbody>
      </table>
      <table class="table table-hover table-dark">
        <thead>
          <tr>
            <th scope="col">Espresso</th>
            <th scope="col">Tên thức uống</th>
            <th scope="col">Giá</th>
            <th scope="col" class="text-center">Tùy chọn</th>
          </tr>
        </thead>
        <tbody v-for="espresso in espressos" :key="espresso.id">
          <tr>
            <th scope="row">
              {{ espresso._id }}
            </th>
            <td>{{ espresso.name }}</td>
            <td>{{ espresso.price }}</td>
            <td>
              <p
                @click="restore(espresso._id)"
                class="btn btn-link btn-restore"
              >
                Khôi phục
              </p>
              <button
                type="button"
                class="btn btn-primary"
                data-toggle="modal"
                data-target="#exampleModal"
                @click="this.id = espresso._id"
              >
                Xóa vĩnh viễn
              </button>
            </td>
          </tr>
        </tbody>
      </table>
    </form>

    <!-- Button trigger modal -->

    <!-- Modal -->
    <div
      class="modal fade show"
      id="exampleModal"
      tabindex="-1"
      role="dialog"
      aria-labelledby="exampleModalLabel"
      aria-hidden="true"
    >
      <div class="modal-dialog" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLabel">Thông báo</h5>
            <button
              type="button"
              class="close"
              data-dismiss="modal"
              aria-label="Close"
            >
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body">Bạn có chắc là xóa sản phẩm không?</div>
          <div class="modal-footer">
            <button
              type="button"
              class="btn btn-secondary"
              data-dismiss="modal"
            >
              Không đồng ý
            </button>
            <button
              type="button"
              class="btn btn-primary"
              data-toggle="modal"
              data-target="#exampleModal"
              @click="deleteItem()"
            >
              Đồng ý
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { swtoast } from "@/mixins/swal.mixin";
import ContactService from "@/services/contact.service";
import axios from "axios";

export default {
  data() {
    return {
      cafes: [],
      phindis: [],
      espressos: [],
      modalShow: false,
      id: "",
    };
  },
  mounted() {
    axios.get("http://localhost:3000/trashMenu").then((response) => {
      console.log("response", response);
      this.cafes = response.data.cafe && response.data.cafe;
      this.phindis = response.data.phindi && response.data.phindi;
      this.espressos = response.data.espresso && response.data.espresso;

      console.log("response", this.cafes, response.cafe, response.data);
    });
  },
  methods: {
    deleteItem() {
      console.log("alo alo", this.id);
      let url = "http://localhost:3000/admin/" + this.id + "/destroyPower";
      axios
        .delete(url, {
          id: this.id,
        })
        .then(() => {
          swtoast.success({
            text: "Xóa sản phẩm thành công",
          });
        });
      this.$router.go(this.$router.currentRoute);
    },
    restore(id) {
      let url = "http://localhost:3000/admin/" + id + "/restore";
      console.log("url", url);
      axios.patch(url, {
        id,
      });
      swtoast.success({
        text: "Khôi phục sản phẩm thành công",
      });
      this.$router.push({ path: "/admin" });
    },
  },
};
</script>
<style>
.body-view {
  min-height: calc(100vh - 189px);
}
</style>
