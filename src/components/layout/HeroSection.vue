<!-- HeroSection component只放頁面大標題 h1、內文 p、按鈕button、img， 及藍色半圓背景塊-->

<script setup></script>

<template>
    <section class="debug w-full">
        <div class="ui-debug my-20 flex flex-col items-center lg:flex-row-reverse">
            <!-- 圖片 -->
            <div class="w-[clamp(200px,50vw,400px)] mx-auto lg:w-[clamp(300px,40vw,500px)]">
                <img src="/src/assets/images/illustration-hero.svg" alt="Hero image" class="w-full">
            </div>
            <!-- 文字 -->
            <div class="ui-debug flex flex-col gap-6 p-6 items-center text-center lg:w-1/2 lg:items-start lg:text-left">
                <h1 className="ui-debug text-[clamp(1.5rem,1rem+3vw,3.5rem)] font-medium text-center lg:text-left max-w-[20ch] leading-tight">A Simple Bookmark Manager</h1>
                <p class="ui-debug text-center text-very-dark-blue/50 font-medium lg:text-left max-w-md">A clean and simple interface to organize your favorite websites. Open a new browser tab and see your sites load instantly. Try it for free.</p>
                <div class="flex items-center justify-center">
                    <button class="">Get it on Chrome</button>
                    <button>Get it on Firefox</button>
                </div>
            </div>
        </div>
    </section>
</template>

<style scoped></style>
