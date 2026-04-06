<!-- TheHeader component只放nav-->

<script setup>
</script>

<template>
    <nav class="container flex items-center justify-between bg-amber-500 px-32 py-6">
        <!-- logo -->
        <div class="logo">
            <img src="/src/assets/images/logo-bookmark.svg" alt="bookmark logo" />
        </div>

        <!-- menu -->
        <ul class="menu">
            <li><a href="#features">Features</a></li>
            <li><a href="#download">Pricing</a></li>
            <li><a href="#contact">Contact</a></li>
        </ul>

        <!-- CTA button -->
        <button class="btn-login">Login</button>
    </nav>
</template>

<style scoped></style>
