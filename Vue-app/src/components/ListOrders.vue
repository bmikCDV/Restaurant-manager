<template>
  <h1>List of orders</h1>
  <div class="orders">
    <div class="order" v-for="order in orders" :key="order.id">
      <h3>Order #{{ order.id }}</h3>
      <ul>
        <li>dishes: {{ order.dishes }}</li>
        <li>table: {{ order.table }}</li>
        <li>notes: {{ order.notes }}</li>
      </ul>
      <button @click.prevent="removeOrder(order.id)" class="delete-btn">Remove order</button>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  props: ["orders"],
  methods: {
    removeOrder(id) {
      console.log("usuwanie zamówienia: ", id);
      axios.delete(`https://localhost:3000/api/private/orders/${id}`).then((response) => response.status);
    },
  },
};
</script>

<style></style>
