<script setup>
  import { ref, onMounted } from 'vue';

  const tabs = ref([]);
  const isLoading = ref(true);
  const activeTab = ref(0);

  onMounted(async () => {
    console.log(activeTab.value)
    try {
      const response = await fetch('/data.json');
      tabs.value = await response.json();
      isLoading.value = false;
      activeTab.value = 0; // Open the first tab/accordion on load
    } catch (error) {
      console.error('Error fetching data:', error);
      isLoading.value = false;
    }
  });
</script>

<template>
  <main class="flex flex-col items-center py-10 px-5 md:px-7 max-w-[650px] mx-auto">
    <div v-if="isLoading" class="text-center">Loading...</div>
    <div v-else class="w-full">
      
      <!-- Tabs for desktop -->
      <div class="hidden md:block">
        <div class="tabs flex flex-col">
          <div class="flex items-center gap-[.55rem] bg-[#3498db] rounded-[6px] h-[52px] py-[.45rem] px-5">
            <button 
              @click="activeTab = index" 
              v-for="(tab, index) in tabs" 
              :key="index"
              :class="{ 'tab--header_active': activeTab === index }"
              class="leading-4 text-[13px] rounded-[30px] bg-[#1f73ac] text-[#d3edff] py-[7px] px-3.5"
            >
              {{ tab.title }}
            </button>
          </div>
          <div class="mt-2 px-5 py-4 border rounded-lg bg-white shadow font-light leading-6" v-html="tabs[activeTab].content"></div>
        </div>
      </div>

      <!-- Accordion for mobile -->
      <div class="block md:hidden bg-white rounded-lg p-5 shadow-lg">
        <div class="accordion">
          <div v-for="(tab, index) in tabs" :key="index" :class="{ 'accordion--item_active': activeTab === index }" class="accordion--item">
            <button 
              @click="activeTab = index" 
              class="accordion--header"
              >
                {{ tab.title }}
                <svg  xmlns="http://www.w3.org/2000/svg"  width="24"  height="24"  viewBox="0 0 24 24"  fill="none"  stroke="#3d3d3d"  stroke-width="2"  stroke-linecap="round"  stroke-linejoin="round"  class="icon icon-tabler icons-tabler-outline icon-tabler-chevron-down"><path stroke="none" d="M0 0h24v24H0z" fill="none"/><path d="M6 9l6 6l6 -6" /></svg>
            </button>
            <div v-show="activeTab === index" class="accordion--content" v-html="tab.content"></div>
          </div>
        </div>
      </div>
      
    </div>
  </main>
</template>

<style scoped lang="scss"></style>
