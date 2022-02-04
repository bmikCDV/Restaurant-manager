<template>
  <h1>Edit Menu</h1>
  <form>
    <input type="number" placeholder="id" v-model="id" />
    <input type="text" placeholder="category" v-model="category" />
    <input type="text" placeholder="dish" v-model="dish" />
    <input type="text" placeholder="description" v-model="description" />
    <input type="number" placeholder="price" v-model="price" />
    <input type="button" value="add to menu" @click.prevent="submit" class="add-btn" />
  </form>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      id: "",
      category: "",
      dish: "",
      description: "",
      price: "",
    };
  },
  methods: {
    submit() {
      console.log(this.dish, this.category, this.description);
      axios
        .post("https://localhost:3000/api/private/menu", {
          id: this.id,
          category: this.category,
          dish: this.dish,
          description: this.description,
          price: this.price,
        })
        .then(function (response) {
          console.log(response);
        })
        .catch(function (error) {
          console.log(error);
        });
      this.id = "";
      this.category = "";
      this.dish = "";
      this.description = "";
      this.price = "";
    },
  },
};
</script>

<style></style>
