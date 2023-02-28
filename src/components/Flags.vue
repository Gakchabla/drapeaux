<script setup>
import FlagFilters from './FlagFilters.vue'
import FlagCard from './FlagCard.vue'
import { ref, watch } from 'vue';

const flags = ref(null)
const filter = ref("")



watch(filter, (newFilter)=>{
    if (newFilter !== "")flags.value = flags.value.filter(flag=>flag.region === newFilter)
})
async function fetchFlags() {
const res = await   fetch("https://restcountries.com/v3.1/all")
    
    flags.value= await res.json()
}
fetchFlags()
</script>

<template>
    <div>
        <FlagFilters />

    </div>
    <div class="flex flex-wrap justify-around "><div v-for="flag in flags" :key="flag.id" class="my-4">
        <FlagCard :country="flag" />
    </div></div>
</template>