<script setup >
import { Gender } from '@/data';

const props = defineProps(['option', 'options'])

</script>   

<template>
    <div class="container-option">

        <p>{{ option.name }}</p>
        <div class="option-button">

            <button v-for="value in option.buttons" :key="value" @click="options[option.category] = value"
                :class="options[option.category] == value && 'option-active'" class="option option-left ">
                {{ value }}
            </button>




        </div>
    </div>
</template>


<style scoped>
</style>