<template>
  <div class="home">
    <h1>Home</h1>
    <h2>Refs</h2>
    <p>My name is {{ person.name }} and my age is {{ person.age }}</p>
    <button @click="handleClick">Update Person</button>
    <h2>Reactive</h2>
    <p>My name is {{ personTwo.name }} and my age is {{ personTwo.age }}</p>
    <button @click="handleClickTwo">Update Person Two</button>
    <h2>Filtering</h2>
    <input type="text" v-model="search">
    <div v-for="name in filteredNames" :key="name">{{ name }}</div>
  </div>
</template>

<script>
import { computed, reactive, ref } from "vue";
// @ is an alias to /src

export default {
  name: "HomeView",
  setup() {
    const person = ref({ name: 'Mario', age: 30})
    const personTwo = reactive({name: 'Luigi', age: 35})
    const names =ref(['mario', 'yoshi', 'sean', 'john', 'steve', 'susan'])
    const search = ref('')

    const filteredNames = computed(() => {
      return names.value.filter((name) => name.includes(search.value))
    })

    const handleClick = () => {
      person.value.age = 40
    };
    const handleClickTwo = () => {
      personTwo.age = 45
    };

    return { person, personTwo, filteredNames, search, handleClick, handleClickTwo };
  },
};
</script>
