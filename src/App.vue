<template>
  <div>
    <header-main />
  </div>
</template>

<script>
import axios from "axios";
import HeaderMain from "./components/Header.vue";
export default {
  props: {
    dictionary_api: {
      type: String,
      default: "https://api.dictionaryapi.dev/api/v2/entries/en/",
    },
  },
  components: {
    HeaderMain,
  },
  methods: {
    async getWord() {
      const response = await axios.get(this.dictionary_api + this.word);
      console.log(response.data);
    },
  },
  data() {
    return {
      word: "",
    };
  },
};
</script>

<style></style>
