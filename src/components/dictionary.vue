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
  <div class="top-left">
    <div class="left">
      <h1 class="word" v-if="result">{{ word }}</h1>
      <p v-if="result" class="phonetic">{{ result[0].phonetic }}</p>
    </div>
    <div class="right">
      <button @click="pronounce" v-if="result" class="play">
        <img
          src="../assets/play.svg"
          alt="purple triangle pointing to the right"
        />
      </button>
    </div>
  </div>

  <h3 v-if="result">Meanings:</h3>
  <ul v-if="result" class="meanings">
    <li v-for="(meaning, index) in result[0].meanings" :key="index">
      <p>
        <strong class="partOfSpeech">{{ meaning.partOfSpeech }}</strong>
      </p>
      <ul>
        <li v-for="(definition, index) in meaning.definitions" :key="index">
          {{ definition.definition }}
          <h4>Synonyms: {{ synonym }}</h4>
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
      this.result = response.data;
    },
    pronounce() {
      const audio = new Audio(this.result[0].phonetics[0].audio);
      audio.play();
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

.play {
  display: flex;
  justify-content: center;
  padding: 10px;
  align-items: center;
  border-radius: 50%;
  border: none;
  cursor: pointer;
  margin-left: 10px;
}

.top-left .left {
  font-family: "Inter", sans-serif;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  text-align: left;
  margin-right: 10px;
}

.top-left {
  font-family: "Inter", sans-serif;
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  width: 100%;
  margin-top: 20px;
  text-align: left;
}

.top-left .word {
  margin-bottom: -17px;
  font-family: "Inter", sans-serif;
}

.phonetic {
  color: #a649ed;
  font-size: 17px;
  text-align: left;
  font-family: "Inter", sans-serif;
}

.partOfSpeech {
  font-family: "Inter", sans-serif;
}

.partOfSpeech::after {
  content: "";
  display: inline-block;
  height: 1px;
  width: 75%;
  background-color: #f5f5f5;
  margin-left: 5px;
  position: relative;
  top: 50%;
  transform: translateY(-50%);
}

.meanings {
  font-family: "Inter", sans-serif;
}
</style>
