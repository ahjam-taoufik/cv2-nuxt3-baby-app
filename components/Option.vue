<script setup lang="ts">
import { Gender, Length, Popularity } from '@/data';

interface propsOptions {
    option: {
        name: string,
        category: string,
        buttons: Gender[] | Popularity[] | Length[]
    },
    options: {
        gender: Gender
        popularity: Popularity
        lenght: Length
    }
}

const props = defineProps<propsOptions>()
// const props = defineProps(['option', 'options'])

const ButtonCalssNames = (value, index) => {
    const ClassNames = []
    if (props.options[props.option.category] == value) ClassNames.push('option-active')
    if (index == 0) ClassNames.push('option-left')
    if (index == props.option.buttons.length - 1) ClassNames.push('option-right')


    return ClassNames.join(' ')
}

</script>   

<template>
    <div class="container-option">

        <p>{{ option.name }}</p>
        <div class="option-button">

            <button v-for="(value, index) in option.buttons" :key="value" @click="options[option.category] = value"
                :class="ButtonCalssNames(value, index)" class="option  ">
                {{ value }}
            </button>




        </div>
    </div>
</template>


<style scoped>
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

/* 
.option:hover {
  background-color: rgb(255, 209, 209)
} */

.option-left {
    border-radius: 1rem 0 0 1rem;
}

.option-right {
    border-radius: 0 1rem 1rem 0;
}

.option-active {
    background-color: rgb(255, 81, 81);
    color: rgb(61, 37, 37)
}
</style>