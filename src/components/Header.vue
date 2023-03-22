<template>
  <div class="header">
    <img src="../assets/logo.svg" alt="dictionary logo" />
    <div class="right">
      <div class="dropdown">
        <button class="font">
          Serif
          <img src="../assets/icon-arrow-down.svg" alt="arrow down icon" />
        </button>

        <div class="dropdown-content">
          <a href="#">Link 1</a>
          <a href="#">Link 2</a>
          <a href="#">Link 3</a>
        </div>
      </div>
      <div id="dark-mode-switch">
        <input type="checkbox" id="switch" name="switch" />
        <label for="switch"></label>
      </div>
      <img src="../assets/icon-moon-light.svg" alt="moon icon" />
    </div>
  </div>
</template>

<script>
export default {
  name: "HeaderMain",
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Inconsolata:wght@400;700&family=Inter:wght@400;700&family=Lora&display=swap");
body {
  background-color: white;
  color: black;
  font-family: "Inter", sans-serif;
}

.header {
  display: flex;
  justify-content: space-between;
  padding-left: 10px;
  padding-right: 10px;
  padding-top: 10px;
}

.right {
  display: flex;
  flex-direction: row;
  align-items: center;
}
.dropdown-content {
  display: none;
}

.font {
  background: transparent;
  border: none;
  border-right: 1px solid gray;
  margin-right: 10px;
  font-size: 17px;
  font-family: inherit;
  font-weight: 700;
  cursor: pointer;
}

.font img {
  margin-left: 5px;
  margin-right: 5px;
}

.dark-mode {
  background-color: black;
  color: white;
}

#dark-mode-switch input[type="checkbox"] {
  display: none;
}

#dark-mode-switch label {
  display: block;
  width: 50px;

  margin-right: 10px;
  height: 23px;
  border-radius: 15px;
  background-color: grey;
  position: relative;
  cursor: pointer;
  transition: background-color 0.2s ease-in-out;
}

#dark-mode-switch label:after {
  content: "";
  display: block;
  position: absolute;
  width: 17px;
  height: 17px;
  border-radius: 50%;
  background-color: white;
  top: 3px;
  left: 2.5px;
  transition: transform 0.2s ease-in-out;
}

#dark-mode-switch input[type="checkbox"]:checked + label {
  background-color: #2196f3;
}

#dark-mode-switch input[type="checkbox"]:checked + label:after {
  transform: translateX(25px);
}
</style>
