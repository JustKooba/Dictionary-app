<template>
  <div>
    <form @submit.prevent="getWord">
      <input
        type="text"
        class="search-a-word"
        v-model="word"
        id="search-a-word"
        placeholder="search a word"
      />
    </form>
  </div>
  <h1 v-if="result">{{ word }}</h1>
  <p v-if="result">{{ result.phonetic }}</p>
  <h2 v-if="result">noun</h2>
  <h3 v-if="result">Meaning</h3>
  <p v-if="result">{{ result }}</p>
  <ul v-if="result">
    <li v-for="(meaning, index) in result.meanings" :key="index">
      <h2>{{ meaning.partOfSpeech }}</h2>
      <ul>
        <li v-for="(definition, index) in meaning.definitions" :key="index">
          {{ definition.definition }}
        </li>
      </ul>
    </li>
  </ul>
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
  data() {
    return {
      word: "",
      result: "",
    };
  },
  methods: {
    async getWord() {
      const response = await axios.get(this.dictionary_api + this.word);
      console.log(response.data);
      this.result = response.data[0].meanings[0].definitions[0].definition;
    },
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
  border-radius: 10px;
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

form {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
