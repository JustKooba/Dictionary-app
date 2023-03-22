<template>
  <div>
    <input
      type="text"
      class="search-a-word"
      v-model="word"
      id="search-a-word"
      placeholder="search a word"
    />
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

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Inconsolata:wght@400;700&family=Inter:wght@400;700&family=Lora&display=swap");
.search-a-word {
  width: 92%;
  height: 20px;
  border: none;
  padding: 10px;
  display: flex;
  margin-top: 20px;
  align-items: center;
  background-color: #f5f5f5;
  border-radius: 7px;
  font-size: 15px;
  font-family: "Inter", sans-serif;
  font-weight: 700;
  color: black;
  outline: none;
  transition: all 0.3s ease;
}

div {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
}
</style>
