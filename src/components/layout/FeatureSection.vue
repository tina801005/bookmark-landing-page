<!-- FeatureSection component只放功能特色內容，包含 次標題h2、內文p、左側藍色半圓背景塊、Feature tabs -->

<script setup>
import FeatureTab from '../ui/FeatureTab.vue';

</script>

<template>
   <section class="w-full my-16  lg:my-32">
      <div class="w-full">
         <div class="flex flex-col items-center gap-6 text-center ">
            <h2>Features</h2>
            <p>Our aim is to make it quick and easy for you to access your favorite websites.
  Your bookmarks sync between your devices so you can access them on the go.</p>
        </div>
        <FeatureTab />
      </div>
   </section>
</template>

<style scoped></style>
