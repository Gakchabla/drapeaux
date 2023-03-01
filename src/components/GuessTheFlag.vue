<script setup>
import { ref } from 'vue';
import GuessTheFlagCard from './GuessTheFlagCard.vue';
import GuessHelp from './GuessHelp.vue'


const flags = ref(null)
const flag = ref({})
const answer = ref("")
const proposition = ref("")
const wrongAnswer = ref(false)
const goodAnswer = ref(false)
const showHelp = ref(false)

function setShowHelp () {showHelp.value = true}


function nextFlag () {goodAnswer.value = false;
    proposition.value=""
getARandomFlag() }





function checkAnswer(e) {
    e.preventDefault()
    if(proposition.value.toLowerCase() === answer.value.toLowerCase()){
        goodAnswer.value = true;
        wrongAnswer.value=false;
        showHelp.value=false;

}
    else{wrongAnswer.value=true
    }
}

async function fetchFlags() {
const res = await   fetch("https://restcountries.com/v3.1/all")
    
    flags.value= await res.json()
    flags.value=flags.value.sort((a,b)=>a.name.common.localeCompare(b.name.common))
}

async function getARandomFlag () {
    await fetchFlags()

flag.value = flags.value[Math.floor(Math.random()*flags.value.length)]
answer.value = flag.value.name.common
}

getARandomFlag()

</script>

<template><div class="flex flex-col items-center justify-center">
    <div class="w-[100vw] h-fit text-4xl text-center my-4">Guess this flag's country!
    </div>
   <GuessTheFlagCard :country="flag" />
<form @submit="checkAnswer" class="flex justify-around items-center my-2 w-[40vw]">
    <input class=" h-10 rounded-xl w-[75%]" type="text" v-model="proposition" placeholder="Type your answer"> <button class="my-2 bg-[#001489] text-xl text-white hover:border-2 hover:border-white w-20 h-10 rounded-xl" type="submit">Submit</button>
</form>
<div v-if="goodAnswer" class="text-[#001489] text-4xl font-bold text-center">Good Answer ! <br/> 
<button @click="nextFlag" class="text-white text-2xl bg-[#001489] hover:border-2 hover:border-white w-fit px-2 h-10 rounded-xl">Next Flag </button></div>
<div v-if="wrongAnswer" class="text-red-600 text-4xl font-bold text-center">Wrong Answer...</div>
<div class="text-center text-2xl"><button @click="setShowHelp">Need Help ? </button><br/>
    <GuessHelp :country="flag" v-if="showHelp" />
</div></div>


</template>