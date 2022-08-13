<script setup lang="ts">
import { Gender, Popularity, Length, names } from '@/data'

interface Options {
  gender: Gender,
  popularity: Popularity,
  lenght: Length
}

const options = reactive<Options>({
  gender: Gender.GIRL,
  popularity: Popularity.TRENDY,
  lenght: Length.LONG
});

const optionsSelected = ref<string[]>([])

const deleteName = (index: number) => {
  // console.log(optionsSelected.value[index]);
  const list = [...optionsSelected.value]
  list.splice(index, 1)

  optionsSelected.value = list

}


const afficheOption = () => {
  const filterNames = names.filter((name) => name.gender == options.gender)
    .filter((name) => name.popularity == options.popularity)
    .filter((name) => {
      if (options.lenght == Length.ALL) return true
      else return name.length == options.lenght
    })

  optionsSelected.value = filterNames.map(name => name.name)
}

const optionArray = [
  {
    name: '1) Choose a gender',
    category: 'gender',
    buttons: [Gender.BOY, Gender.GIRL, Gender.UNISEX]
  },
  {
    name: "2) Choose the name's popularity",
    category: 'popularity',
    buttons: [Popularity.TRENDY, Popularity.UNIQUE]
  },
  {
    name: "3) Choose name's lenght",
    category: 'lenght',
    buttons: [Length.LONG, Length.ALL, Length.SHORT]
  },
]
</script>

<template>
  <!-- <NuxtWelcome /> -->
  <div class="container">
    <h1>Baby Name Generator</h1>
    <h2>Choose your options click the "Find Names" buttom below</h2>
    <div class="container-options">

      <Option v-for="option in optionArray" :key="option.name" :option="option" :options="options" />

      <!-- <div class="container-option">

        <p>1) Choose a gender</p>
        <div class="option-button">

          <button @click="options.gender = Gender.BOY" :class="options.gender == Gender.BOY && 'option-active'"
            class="option option-left ">Boy
          </button>

          <button @click="options.gender = Gender.UNISEX" :class="options.gender == Gender.UNISEX && 'option-active'"
            class="option">Unisex
          </button>

          <button @click="options.gender = Gender.GIRL" :class="options.gender == Gender.GIRL && 'option-active'"
            class="option option-right ">Girl
          </button>

        </div>
      </div> -->
      <!-- <div class="container-option">
        <p>2) Choose the name's popularity</p>
        <div class="option-button">

          <button @click="options.popularity = Popularity.TRENDY"
            :class="options.popularity == Popularity.TRENDY && 'option-active'"
            class="option option-left">Trendy</button>
          <button @click="options.popularity = Popularity.UNIQUE"
            :class="options.popularity == Popularity.UNIQUE && 'option-active'"
            class="option option-right">Unique</button>

        </div>
      </div> -->
      <!-- <div class="container-option">
        <p>3) Choose name's lenght</p>
        <div class="option-button">

          <button @click="options.lenght = Length.LONG" :class="options.lenght == Length.LONG && 'option-active'"
            class="option option-left">Long</button>
          <button @click="options.lenght = Length.ALL" :class="options.lenght == Length.ALL && 'option-active'"
            class="option">All</button>

          <button @click="options.lenght = Length.SHORT" :class="options.lenght == Length.SHORT && 'option-active'"
            class="option option-right">Short</button>

        </div>
      </div> -->


      <button @click="afficheOption" class="option option-select">select</button>

    </div>

    <div class="container-cards">
      <CardName v-for="(name, index) in optionsSelected" :key="name" :name="name" :index="index"
        @deleteName="deleteName(index)" />
      <!-- <div class="card" v-for="name in optionsSelected" :key="name">
        {{ name }}
        <p>X</p>
      </div> -->


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
  cursor: pointer;
}

.option-select {
  margin-top: 1rem;
  border-radius: 1rem
}

.option-select:hover {
  background-color: rgb(248, 93, 93)
}

.container-cards {
  /* background-color: rgb(241, 145, 145); */
  display: flex;
  flex-wrap: wrap;
}
</style>