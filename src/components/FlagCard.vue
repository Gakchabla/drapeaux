<script setup>
const props = defineProps({
  country: Object
})</script>

<template>
<div class="h-52 w-80 bg-black object-contain"><div class="h-52 w-80 bg-black absolute bg-opacity-0 text-2xl text-transparent hover:bg-opacity-50 hover:text-white flex justify-center items-center">{{country.name.common}}</div><img :src="country.flags.png" alt="" class="h-52 w-80 object-fit overflow-hidden" /></div>
</template>