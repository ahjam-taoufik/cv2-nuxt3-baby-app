<script setup lang="ts">

enum Gender {
  BOY = "Boy",
  GIRL = 'Girl',
  UNISEX = 'Unisex'
}

enum Popularity {
  TRENDY = 'Trendy',
  UNIQUE = 'Unique'
}

enum Lenght {
  LONG = 'Long',
  ALL = 'All',
  SHORT = 'Short'
}

interface Options {
  gender: Gender,
  popularity: Popularity,
  lenght: Lenght
}

const options = reactive<Options>({
  gender: Gender.GIRL,
  popularity: Popularity.TRENDY,
  lenght: Lenght.LONG
});
</script>

<template>
  <!-- <NuxtWelcome /> -->
  <div class="container">
    <h1>Baby Name Generator</h1>
    <h2>Choose your options click the "Find Names" buttom below</h2>
    <div class="container-options">
      <div class="container-option">
        <p>1) Choose a gender</p>
        <div class="option-button">

          <button @click="options.gender = Gender.BOY" :class="options.gender == Gender.BOY && 'option-active'"
            class="option option-left ">Boy
          </button>
          <button @click="options.gender = Gender.UNISEX" :class="options.gender == Gender.UNISEX && 'option-active'"
            class="option">Unisex</button>
          <button @click="options.gender = Gender.GIRL" :class="options.gender == Gender.GIRL && 'option-active'"
            class="option option-right ">Girl</button>

        </div>
      </div>
      <div class="container-option">
        <p>2) Choose the name's popularity</p>
        <div class="option-button">

          <button @click="options.popularity = Popularity.TRENDY"
            :class="options.popularity == Popularity.TRENDY && 'option-active'"
            class="option option-left">Trendy</button>
          <button @click="options.popularity = Popularity.UNIQUE"
            :class="options.popularity == Popularity.UNIQUE && 'option-active'"
            class="option option-right">Unique</button>

        </div>
      </div>
      <div class="container-option">
        <p>3) Choose name's lenght</p>
        <div class="option-button">

          <button @click="options.lenght = Lenght.LONG" :class="options.lenght == Lenght.LONG && 'option-active'"
            class="option option-left">Long</button>
          <button @click="options.lenght = Lenght.ALL" :class="options.lenght == Lenght.ALL && 'option-active'"
            class="option">All</button>

          <button @click="options.lenght = Lenght.SHORT" :class="options.lenght == Lenght.SHORT && 'option-active'"
            class="option option-right">Short</button>

        </div>
      </div>

    </div>
  </div>
</template>

<style scoped>
h1 {
  font-size: 50px;
}

.container {
  /* background: rgb(255, 192, 192); */
  color: rgb(14, 82, 119);
  text-align: center;
  margin: 0 auto;
  max-width: 70%;
  font-family: Arial, Helvetica, sans-serif;
}

.container-options {
  background-color: rgb(201, 235, 241);
  color: rgb(44, 53, 58);
  font-weight: bold;
  border-radius: 20px;
  padding: 10px;
}

.option {
  width: 170px;
  padding: 10px 0;
  border: none;
  outline: 2px solid red;
  background-color: aliceblue;
  font-weight: bold;
  font-size: 17px;
}

.option:hover {
  background-color: rgb(255, 209, 209)
}

.option-left {
  border-radius: 1rem 0 0 1rem;
}

.option-right {
  border-radius: 0 1rem 1rem 0;
}

.option-active {
  background-color: rgb(255, 81, 81);
  color: whitesmoke
}
</style>