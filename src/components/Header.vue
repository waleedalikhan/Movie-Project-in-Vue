<template>
  <header>
    <router-link to="/">
      <h1>{{ headerName }}</h1>
    </router-link>
  </header>
</template>

<script>
export default {
  data() {
    return {
      headerName: "The Movie DB"
    };
  }
};
</script>

<style scoped>
header {
  background-color: #111;
  padding: 20px;
  color: #fff;
}

h1 {
  margin: 0;
}
</style>