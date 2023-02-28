<script setup>
import FlagCard from './FlagCard.vue'
import { ref, watch, computed} from 'vue';

const flags = ref(null)
const search = ref("")
const checkedContinent = ref([])

const filteredFlags = computed(()=> {
return search.value ? flags.value.filter(flag => flag.name.common.toLowerCase().includes(search.value.toLowerCase())) : flags.value;
})

watch(checkedContinent, async (newCheckedContinent)=>{
     const checked = await JSON.parse(JSON.stringify(newCheckedContinent))
    await fetchFlags()
    if (checked.length > 0){flags.value = flags.value.filter(flag=>newCheckedContinent.includes(flag.region))}
else{fetchFlags}})



async function fetchFlags() {
const res = await   fetch("https://restcountries.com/v3.1/all")
    
    flags.value= await res.json()
    flags.value=flags.value.sort((a,b)=>a.name.common.localeCompare(b.name.common))
}
fetchFlags()
</script>

<template>
    <div>
        <div class="flex  flex-wrap  justify-around h-fit md:h-12 lg:h-12 text-2xl items-center min-h-fit">
    <div class="flex justify-around items-center"><input class="mx-2" type="checkbox" name="Africa" value="Africa" v-model="checkedContinent">
    <label for="Africa"> Africa</label> </div>
    <div class="flex justify-around items-center"><input class="mx-2" type="checkbox" name="Americas" value="Americas" v-model="checkedContinent">
    <label for="Americas"> Americas</label></div>
    <div class="flex justify-around items-center"><input class="mx-2" type="checkbox" name="Asia" value="Asia" v-model="checkedContinent">
    <label for="Asia"> Asia</label></div>
    <div class="flex justify-around items-center"><input class="mx-2" type="checkbox" name="Europe" value="Europe" v-model="checkedContinent">
    <label for="Europe"> Europe</label></div>
    <div class="flex justify-around items-center"><input class="mx-2" type="checkbox" name="Oceania" value="Oceania" v-model="checkedContinent">
    <label for="Oceania"> Oceania</label></div></div> 
    </div>
    <div class="flex justify-center w-[100vw] h-8"><input type="text" v-model="search" placeholder="Search a country" ></div>
    <div class="flex flex-wrap justify-around "><div v-for="flag in filteredFlags" :key="flag.name.common" class="my-4">
        <FlagCard :country="flag" />
    </div></div>
</template>