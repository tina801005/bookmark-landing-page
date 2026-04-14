<!-- TheHeader component只放nav-->

<script setup>
</script>

<template>
    <!-- 最外層 -->
    <nav class="w-full flex justify-between">
        <!-- mobile和table都通用的外logo -->
        <div class="logo">
            <img src="/src/assets/images/logo-bookmark.svg" alt="bookmark logo">
        </div>
        <!-- mobile 漢堡選單icon lg:隱藏 -->
        <button class="h-7 cursor-pointer lg:hidden" aria-label="Menu" aria-expanded="false" aria-controls="mobile-menu">
            <span class="sr-only">Open main menu</span>
            <img src="/src/assets/images/icon-hamburger.svg" alt="hamburger mobile menu icon">
        </button>

        <!-- table menu lg:顯示 -->
        <ul class=" hidden gap-6 justify-center items-center lg:flex">
            <li class="menu-item-font menu-list-item">FEATURES</li>
            <li class="menu-item-font menu-list-item">PRICING</li>
            <li class="menu-item-font menu-list-item">CONTACT</li>
            <button class="login-btn">LOGIN</button>
        </ul>

        <!-- mobile menu -->
        <div id="mobile-menu" class="hidden fixed top-0 left-0 right-0 bottom-0 w-full bg-very-dark-blue/90  flex-col p-7">

            <div class="flex justify-between">
                <div class="mobile-logo cursor-pointer" href="#">
                    <img src="/src/assets/images/logo-bookmark-mobile.svg" alt="mobile bookmark logo">
                </div>
                <button id="J_closeBtn" class="cursor-pointer" aria-label="Close menu" aria-expanded="true" aria-controls="mobile-menu">
                    <img src="/src/assets/images/icon-close.svg" alt="close menu icon">
                </button>
            </div>

            <ul class=" flex flex-col items-center justify-center mt-10">
                <li class="mobile-menu-item mobile-menu-text-style hover:text-soft-red hover:transition hover:delay-100" href="#">FEATURES</li>
                <li class="mobile-menu-item mobile-menu-text-style hover:text-soft-red hover:transition hover:delay-100" href="#">PRICING</li>
                <li class="mobile-menu-item mobile-menu-text-style hover:text-soft-red hover:transition hover:delay-100" href="#">CONTACT</li>
                <button class="mobile-login-btn mobile-menu-text-style" >LOGIN</button>

            </ul>

            <div class="flex items-center justify-center mt-50 gap-6">
                <img src="/src/assets/images/icon-facebook.svg" alt="Facebook" class="social-icon">
                <img src="/src/assets/images/icon-twitter.svg" alt="Twitter" class="social-icon">
            </div>

        </div>

    </nav>

</template>

<style scoped></style>
