<template>
  <div>
    <header-main />
    <dictionary v-on:toggleDarkMode="toggleDarkMode" />
  </div>
</template>

<script>
import HeaderMain from "./components/Header.vue";
import dictionary from "./components/dictionary.vue";
export default {
  components: {
    HeaderMain,
    dictionary,
  },
};
</script>

<style></style>
