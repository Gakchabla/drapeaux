<script setup>
import { ref } from 'vue';

const props = defineProps({
  country: Object});

const showContinent = ref(false)
const showCapital = ref(false)
const showAnswer = ref(false)

function setShowCapital () {showCapital.value = true}
function setShowContinent () {showContinent.value = true}
function setShowAnswer () {showAnswer.value = true}
</script>

<template><div class="text-start flex w-[40vw] min-w-fit justify-around"><div class="min-w-fit">Here are some hint :
    <div v-if="showContinent" class="min-w-fit"> Continent : {{ country.region ? country.region : "" }}</div>
    <div v-else class="min-w-fit">Continent : <button @click="setShowContinent" class="text-xl text-white  bg-[#001489] px-2 rounded-lg">Show </button></div>
    <div v-if="showCapital" class="min-w-fit"> Capital City : {{ country.capital ? country.capital[0] : "" }}</div>
    <div v-else class="min-w-fit">Capital City : <button @click="setShowCapital" class="text-xl text-white  bg-[#001489] px-2 rounded-lg">Show </button></div>
</div><div class="text-center">Still no idea? <br/> Here's the answer: <br/>
    <div v-if="showAnswer">{{ country.name.common }}</div>
    <div v-else><button @click="setShowAnswer" class="text-xl text-white  bg-[#001489] px-2 rounded-lg">Show</button></div></div></div>
    </template>