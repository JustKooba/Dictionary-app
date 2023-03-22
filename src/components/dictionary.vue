<template>
  <div>
    <input type="text" v-model="word" id="search-a-word" />
    <label for="search-a-word"></label>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Dictionary",
  props: {
    dictionary_api: {
      type: String,
      default: "https://api.dictionaryapi.dev/api/v2/entries/en/",
    },
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
