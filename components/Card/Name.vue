<script setup lang="ts">
interface NameProps {
    name: string
}
const props = defineProps<NameProps>()
</script>


<template>
    <div class="card">
        {{ name }}
        <p>X</p>
    </div>
</template>


<style  scoped>
.card {
    background-color: rgb(87, 118, 253);
    margin-left: 20px;
    padding: 16px 40px;
    color: white;
    border-radius: 1rem;
    margin-top: 1rem;
    position: relative
}

.card p {
    /* background-color: aqua; */
    position: absolute;
    top: -13px;
    right: 11px;
    font-weight: bold;
    cursor: pointer;
}
</style>