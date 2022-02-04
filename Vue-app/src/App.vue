<template>
  <h1 id="header">Restaurant Managing App</h1>
  <div class="options">
    <button @click="showMenu" class="option-btn">View Menu</button>
    <button @click="showEditMenu" class="option-btn">Add to Menu</button>
    <button @click="showPlaceOrder" class="option-btn">Add Order</button>
    <button @click="showOrders" class="option-btn">List Orders</button>
  </div>
  <!-- <h1>{{ menu_elems }}</h1> -->
  <Order v-if="show_order" />
  <Menu v-if="show_menu" :menu="this.menu_elems" />
  <AddMenu v-if="show_edit_menu" />
  <ListOrders v-if="show_orders" :orders="orders" />
</template>

<script>
import axios from "axios";
import Order from "./components/Order.vue";
import Menu from "./components/Menu.vue";
import AddMenu from "./components/AddMenu.vue";
import ListOrders from "./components/ListOrders.vue";
export default {
  name: "Restaurant",
  data() {
    return {
      show_menu: false,
      show_edit_menu: false,
      show_order: false,
      show_orders: false,
      menu_elems: "",
      orders: "",
    };
  },
  components: {
    Order,
    Menu,
    ListOrders,
    AddMenu,
  },
  methods: {
    showMenu() {
      //showing one element and hiding others
      this.show_menu = !this.show_menu;
      this.show_edit_menu = false;
      this.show_order = false;
      this.show_orders = false;
      axios
        .get("https://localhost:3000/api/private/menu/all")
        .then((response) => {
          this.menu_elems = response.data.data;
        })
        .catch((er) => console.log(er));
    },
    showOrders() {
      //showing one element and hiding others
      this.show_orders = !this.show_orders;
      this.show_order = false;
      this.show_menu = false;
      this.show_edit_menu = false;
      axios
        .get("https://localhost:3000/api/private/orders/all")
        .then((response) => {
          console.log(response.data);
          this.orders = response.data.data;
        })
        .catch((er) => console.log(er));
    },
    showPlaceOrder() {
      //showing one element and hiding others
      this.show_order = !this.show_order;
      this.show_orders = false;
      this.show_menu = false;
      this.show_edit_menu = false;
    },
    showEditMenu() {
      //showing one element and hiding others
      this.show_edit_menu = !this.show_edit_menu;
      this.show_menu = false;
      this.show_order = false;
      this.show_orders = false;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
