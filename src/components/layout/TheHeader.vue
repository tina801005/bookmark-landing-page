<!-- TheHeader component只放nav-->

<script setup>
</script>

<template>
    <nav class="debug container flex items-center justify-between py-6 font-base">
        <!-- logo -->
        <div class="debug logo flex-1">
            <img src="/src/assets/images/logo-bookmark.svg" alt="bookmark logo" />
        </div>

        <!-- menu -->
        <ul class="debug menu ">
            <li class="ui-debug button-style  hover:text-red-400"><a href="#features">Features</a></li>
            <!-- <li class="ui-debug "><a href="#download">Pricing</a></li>
            <li class="ui-debug "><a href="#contact">Contact</a></li> -->
        </ul>



        <!-- CTA button -->
        <button class="ui-debug btn-login block py-9">Login</button>
    </nav>
</template>

<style scoped></style>
