<template>
    <div class="flex flex-col p-8">
        <input type="text" class="rounded border-2 border-grey-200 w-full" placeholder="Search For Meals"/>

        <div class="flex justify-center gap-2 mt-2 gap-1">
            <router-link :to="{name: 'byLetter', params: {letter}}" v-for="letter of letters" :key="letter">
                {{ letter }}
            </router-link>
        </div>
    </div>

    
</template>

<script setup>
import { computed, onMounted, ref } from 'vue';
import store from '../store'
import axiosClient from '../axiosClient.js'

const letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split("");
const ingredients = ref([])

onMounted(async () => {
    const response = await axiosClient.get('/list.php?i=list')
    console.log(response.data)
    ingredients.value = response.data
})
</script>

<style scoped>

</style>