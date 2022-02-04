<template>
  <h1>Menu View</h1>
  <div class="dishes">
    <div class="menu-elem" v-for="dish in menu" :key="dish.id">
      <h3>{{ dish.dish }}</h3>
      <ul>
        <li>Category: {{ dish.category }}</li>
        <li>{{ dish.description }}</li>
        <li>{{ dish.price }} Złociszy polskich</li>
      </ul>
      <button @click.prevent="removeDish(dish.id)" class="delete-btn">Remove dish</button>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  props: ["menu"],
  methods: {
    removeDish(id) {
      console.log("usuwanie dania: ", id);
      axios.delete(`https://localhost:3000/api/private/menu/${id}`).then((response) => response.status);
    },
  },
};
</script>

<style>
/* App header */
#header {
  font-size: 3rem;
}
/* option buttons cotainer */
.options {
  display: flex;
  justify-content: center;
  gap: 1rem;
  margin: 1rem 0;
}
/* List of menu items */
.menu-elem,
.order {
  display: flex;
  flex-direction: column;
  align-items: center;
}
/* headers */
h1 {
  margin-bottom: 0;
}
h3 {
  text-transform: uppercase;
  margin-bottom: 0;
}
/* unordered lists */
ul {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  padding: 0;
}
ul > * {
  padding: unset;
  text-orientation: initial;
}
/* FORM */
form {
  margin-top: 2rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
}
form input {
  transition: linear 0.2s;
  padding: 0.5rem 1rem;
  border-radius: 1.5rem;
}
form input:focus {
  background-color: rgb(212, 239, 250);
}
/*  delete button */
.delete-btn,
.option-btn,
.add-btn {
  transition: linear 0.3s;
  padding: 0.75rem 1rem;
  max-width: max-content;
  text-transform: capitalize;
  background-color: #f05148;
  color: rgb(235, 235, 238);
  border: 3px solid rgb(235, 235, 238);
  border-radius: 2rem;
}
.delete-btn:hover {
  background-color: #cc2820;
  cursor: pointer;
}

/* blue option buttons */
.option-btn {
  background-color: #2986f0;
}
.option-btn:hover {
  background-color: #2255b3;
  cursor: pointer;
}
/* add button */
.add-btn {
  background-color: #1da752;
}
.add-btn:hover {
  background-color: #0e8f4e;
  cursor: pointer;
}
</style>
