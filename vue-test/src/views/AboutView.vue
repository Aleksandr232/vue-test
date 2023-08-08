

<template>
  <div class="other-page">
    <h1>Другая страница</h1>
    <div>{{ name }}</div>
    <div>{{ age }}</div>
    <div v-for="(child, index) in children" :key="index">
      <div>{{ child.name }}</div>
      <div>{{ child.age }}</div>
    </div>
  </div>
</template>

<script>
  export default {
  mounted() {
    // Извлекаем параметры из URL
    this.name = this.$route.params.name;
    this.age = this.$route.params.age;
    this.children = JSON.parse(this.$route.params.children);
  },
  data() {
    return {
      name: '',
      age: '',
      children: ''
    }
  }
}        
</script>

<style>

</style>
