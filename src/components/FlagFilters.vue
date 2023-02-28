<script setup>

function onInput(e) {
  console.log(e.checked)
}</script>

<template>
   <div class="flex justify-around">
    <div><input type="checkbox" name="Africa" value="Africa" @change="onInput">
    <label for="Africa"> Africa</label> </div>
    <div><input type="checkbox" name="America" value="America">
    <label for="America"> America</label></div>
    <div><input type="checkbox" name="Asia" value="Asia">
    <label for="Asia"> Asia</label></div>
    <div><input type="checkbox" name="Europe" value="Europe">
    <label for="Europe"> Europe</label></div>
    <div><input type="checkbox" name="Oceania" value="Oceania">
    <label for="Oceania"> Oceania</label></div></div> 
</template>