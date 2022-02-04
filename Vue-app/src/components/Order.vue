<template>
  <h1>Placing Order</h1>
  <form>
    <input type="number" placeholder="id" v-model="id" />
    <input type="text" placeholder="dishes" v-model="dishes" />
    <input type="number" placeholder="table" v-model="table" />
    <input type="text" placeholder="notes" v-model="notes" />
    <input type="number" placeholder="PLN_price" v-model="PLN_price" />
    <input type="button" value="submit" @click.prevent="submit" class="add-btn" />
  </form>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      id: "",
      dishes: "",
      table: "",
      notes: "",
      PLN_price: "",
    };
  },
  methods: {
    submit() {
      console.log(this.dish, this.table, this.notes);
      axios
        .post("https://localhost:3000/api/private/orders", {
          id: this.id,
          table: this.table,
          dishes: this.dishes,
          notes: this.notes,
          PLN_price: this.PLN_price,
        })
        .then(function (response) {
          console.log(response);
        })
        .catch(function (error) {
          console.log(error);
        });
      this.dishes = "";
      this.table = "";
      this.notes = "";
      this.PLN_price = "";
      this.id = "";
    },
  },
};
</script>

<style></style>
