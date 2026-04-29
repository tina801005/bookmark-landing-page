<!-- HeroSection component只放頁面大標題 h1、內文 p、按鈕button、img， 及藍色半圓背景塊-->

<script setup>
import BgBlueRect from "../ui/BgBlueRect.vue";
</script>

<template>
    <section class="w-full relative">

        <div class="my-10 flex flex-col items-center lg:flex-row-reverse lg:my-20 md:my-10">
            <!-- 圖片 -->
            <div class="relative w-[90%] lg:mb-0 lg:w-1/2 flex justify-center">
                <img src="/src/assets/images/illustration-hero.svg" alt="Hero image" class="w-full">
                <BgBlueRect class="rounded-l-full -right-[10%] w-[75vw] h-[70%] top-1/3 lg:h-[80%] lg:-right-[20%] lg:w-[35vw] lg:top-1/4 md:w-[60vw]"/>
            </div>
            <!-- 文字 -->
            <div class="flex flex-col gap-6 p-6 items-center text-center lg:w-1/2 lg:items-start lg:text-left">
                <h1 class="text-[clamp(2rem,1rem+3vw,3.5rem)] font-medium text-center lg:text-left max-w-[20ch] leading-tight">A Simple Bookmark Manager</h1>
                <p class="px-10 text-center text-very-dark-blue/50 font-medium lg:text-left lg:px-0 max-w-md">A clean and simple interface to organize your favorite websites. Open a new browser tab and see your sites load instantly. Try it for free.</p>
                <div class="flex gap-3 ">
                    <button class="p-3 rounded-lg bg-soft-blue text-white-gray cursor-pointer border-2 border-transparent font-medium shadow-lg hover:bg-white-gray hover:text-soft-blue hover:border-soft-blue">Get it on Chrome</button>
                    <button class="p-3 rounded-lg bg-white-gray text-very-dark-blue cursor-pointer border-2 border-transparent font-medium shadow-lg hover:bg-white-gray hover:text-very-dark-blue hover:border-very-dark-blue">Get it on Firefox</button>
                </div>
            </div>
        </div>

    </section>
</template>

<style scoped></style>
