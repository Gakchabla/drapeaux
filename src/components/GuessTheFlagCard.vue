<script setup>
const props = defineProps({
  country: Object
})</script>

<template>
<div class="h-[27vw] w-[40vw] bg-black object-contain"><img :src="country.flags ? country.flags.png : null" alt="" class="h-full w-full object-fit overflow-hidden" /></div>
</template>