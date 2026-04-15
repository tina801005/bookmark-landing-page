<!-- TheHeader component只放nav-->

<script setup lang="ts">
import { ref } from 'vue'; // 引入ref來創建響應式變量

// menu選單控制相關的變量和函數
const currentPage = ref<string>('currentPage.value'); // 定義一個響應式變量來追蹤當前頁面，初始值為'Features'

// 定義導航連結的數據，這裡使用一個陣列來存儲每個連結的名稱和對應的URL
const navLinks = [
  { name: 'Features', href: '#features' },
  { name: 'Pricing', href: '#pricing' },
  { name: 'Contact', href: '#contact' }
];

// 模擬登入按鈕的點擊事件，目前只是彈出一個提示，實際功能待開發
const handleLoginClick = () => {
  alert('Login feature under development');
};

//漢堡選單開合與關閉按鈕交互
const isMenuOpen = ref(false); // 專門控制開合的開關

// 定義一個函數來切換mobile menu的開合狀態
const toggleMobileMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};

</script>

<template>
    <!-- 最外層 -->
    <nav class="w-full flex justify-between items-center" aria-label="main navigation">
        <!-- mobile和table都通用的外logo -->
        <div>
            <a href="/" aria-label="Bookmark Home" class="focus-others">
                <img src="/src/assets/images/logo-bookmark.svg" alt="" aria-hidden="true">
            </a>
        </div>
        <!-- mobile 漢堡選單icon lg:隱藏 -->
        <button id="T_menu"
        class="focus-others w-5 h-5 cursor-pointer lg:hidden"
        aria-label="mobile menu"
        aria-controls="mobile-menu"
        :aria-expanded="isMenuOpen"
        @click="toggleMobileMenu">
            <span class="sr-only">Open main menu</span>
            <img src="/src/assets/images/icon-hamburger.svg" alt="hamburger mobile menu icon" class="pointer-events-none w-full h-full">
        </button>
        <!-- table menu lg:顯示 -->
        <ul class=" hidden gap-6 justify-center items-center lg:flex" role="menubar" aria-label="Primary">
            <li v-for="link in navLinks"
            :key="link.name"
            class="menu-item-font menu-list-item" >
                <a :href="link.href"
                :aria-current="currentPage === link.name ? 'page' : undefined"
                class="focus-link"
                >{{ link.name }}</a>
            </li>
            <li>
                <button @click="handleLoginClick" class="login-btn focus-button" >LOGIN</button>
            </li>
        </ul>
        <!-- mobile menu -->
        <div id="mobile-menu" class="mobile-menu-background" v-if="isMenuOpen" role="dialog" aria-modal="true">

            <div class="flex justify-between">
                <div class="mobile-logo cursor-pointer">
                    <a href="/" aria-label="Bookmark Home" class="focus-others">
                        <img src="/src/assets/images/logo-bookmark-mobile.svg" alt="mobile bookmark logo">
                    </a>

                </div>
                <button id="T_closeBtn" class="focus-others close-btn cursor-pointer" aria-label="Close menu" :aria-expanded="isMenuOpen" aria-controls="mobile-menu" @click="toggleMobileMenu">
                    <img src="/src/assets/images/icon-close.svg" alt="close menu icon">
                </button>
            </div>
            <ul class=" flex flex-col items-center justify-center mt-10">
                <li v-for="link in navLinks"
                :key="link.name"
                class="mobile-menu-item mobile-menu-text-style hover:text-soft-red hover:transition hover:delay-100" >
                    <a :href="link.href"
                    :aria-current="currentPage === link.name ? 'page' : undefined"
                    class="focus-link"
                    >{{ link.name }}</a>
                </li>
                <li>
                    <!-- 因為這裡我只要button有樣式，所以li刻意不加任何class -->
                    <button @click="handleLoginClick" class="mobile-login-btn mobile-menu-text-style focus-button" >LOGIN</button>
                </li>
            </ul>
            <div class="flex items-center justify-center mt-50 gap-6" aria-label="social media links">
                <a href="#" aria-label="Facebook">
                    <img src="/src/assets/images/icon-facebook.svg" alt="Facebook" class="social-icon">
                </a>
                <a href="#" aria-label="Twitter">
                    <img src="/src/assets/images/icon-twitter.svg" alt="Twitter" class="social-icon">
                </a>
            </div>
        </div>
    </nav>
</template>

<style scoped></style>
