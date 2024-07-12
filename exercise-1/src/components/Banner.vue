<script setup>
  import { defineProps } from 'vue';

  defineProps({
    title: String,
  })
</script>

<template>
  <header class="relative w-full header">
    <img src="https://via.placeholder.com/1920x650" alt="Hero Banner" class="w-full h-auto header__desktop" />
    <img src="https://via.placeholder.com/600x600" alt="Hero Banner" class="w-full h-auto header__mobile" />
    <div class="absolute top-0 left-0 w-full h-full flex flex-col items-center justify-center text-center bg-black bg-opacity-35 px-7 header__detail">
      <h1 class="text-white text-5xl font-bold">{{ title }}</h1>
      <p class="text-white text-2xl mt-4 font-thin tracking-wider">Lorem ipsum dolor sit amet, consectetur adipiscing elit</p>
    </div>
  </header>
</template>

<style scoped lang="scss"></style>
