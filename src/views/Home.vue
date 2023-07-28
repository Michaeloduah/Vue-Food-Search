<template>
    <div class="flex flex-col p-8">
        <input type="text" class="rounded border-2 border-grey-200 w-full" placeholder="Search For Meals"/>
    </div>

    <div class="flex justify-center gap-2 mt-2 gap-1">
        <router-link :to="{name: 'byLetter', params: {letter}}" v-for="letter of letters" :key="letter">
            {{ letter }}
        </router-link>
    </div>
</template>

<script setup>
import { computed } from 'vue';
import store from '../store'


const meals = computed(() => store.state.meals)
const letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split("");

</script>

<style scoped>

</style>