<!-- FeatureSection component只放功能特色內容，包含 次標題h2、內文p、左側藍色半圓背景塊、Feature tabs -->

<script setup>
import FeatureTab from '../ui/FeatureTab.vue';

</script>

<template>
   <section class="w-full">
      <div class="w-full">
         <div class=" flex flex-col items-center gap-6 text-center my-20 lg:my-32">
            <h2 class="text-very-dark-blue text-[clamp(2rem,1rem+3vw,2.5rem)] font-medium">Features</h2>
            <p class="px-10 text-center text-very-dark-blue/50 font-medium max-w-md lg:px-0">Our aim is to make it quick and easy for you to access your favorite websites.
  Your bookmarks sync between your devices so you can access them on the go.</p>
        </div>
        <FeatureTab />
      </div>
   </section>
</template>

<style scoped></style>
