<script setup>
  import { ref, onMounted } from 'vue';

  const cards = ref([]);
  const isLoading = ref(true);

  const readMore = (e) => {
    e.preventDefault();
    alert('Read more clicked!');
  };

  onMounted(async () => {
    try {
      const response = await fetch('/data.json');
      cards.value = await response.json();
      isLoading.value = false;
    } catch (error) {
      console.error('Error fetching data:', error);
    } finally {
      isLoading.value = false;
    }
  });
</script>

<template>
  <main class="flex flex-col items-center py-10 px-5 md:px-7">
    <div v-if="isLoading">Loading...</div>
    <div v-else class="grid grid-cols-1 md:grid-cols-3 gap-6 md:gap-10">
      <div v-for="card in cards" :key="card.id" class="bg-white shadow-lg border-[1px] text-gray-100 border-slate-100 rounded-lg overflow-hidden max-w-sm flex flex-col">
        <div class="p-5 pb-0">
          <img :src="card.image" :alt="'Card Image ' + card.id" class="w-full h-auto" />
        </div>
        <div class="p-5 text-center h-full flex flex-col justify-between">
          <p class="text-gray-700 text-base">
            {{ card.description }}
          </p>
          <a href="/" @click="readMore" class="border-2 text-gray-900 border-slate-900 hover:bg-slate-800 hover:text-white transition-all mt-4 font-bold uppercase tracking-wider py-2 px-4 rounded-full inline-flex mx-auto">
            Read More
          </a>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped lang="scss"></style>