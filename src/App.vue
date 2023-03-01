<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header class="bg-[#eee] h-auto min-h-[100vh]">
    <div class="flex flex-wrap justify-center items-center bg-[#001489] pb-2 border-b-2 text-[#eee] border-black w-[100vw] h-28">
      <h1 class="text-6xl text-center w-full">FLAGS</h1>
<div class=" w-1/5 min-w-fit text-2xl flex justify-center"><RouterLink to="/" class="mx-4" >Flags</RouterLink>
<RouterLink to="/guess" class="mx-4" >Guess The Flag</RouterLink></div>

    </div>
<RouterView />
  </header>

</template>

<style scoped>
.router-link-active{
  text-decoration: underline;
}
</style>
