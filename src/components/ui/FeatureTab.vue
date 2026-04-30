<!-- FeatureTab component只放功能特色標籤，包含左側img+右側項目標題h3 + 內文p-->

<script setup></script>

<template>
    <div>
        <ul class="w-[75%] mx-auto flex flex-col justify-center items-center border-y border-very-dark-blue/20 lg:flex-row lg:border-y-0 lg:border-b">
            <li class="w-full py-4 grid place-items-center cursor-pointer  lg:border-very-dark-blue/20  hover:text-soft-red"><button class="cursor-pointer">Simple Bookmarking</button></li>
            <li class="w-full py-4 grid place-items-center cursor-pointer border-y border-very-dark-blue/20 lg:border-y-0  hover:text-soft-red"><button class="cursor-pointer">Speedy Searching</button></li>
            <li class="w-full py-4 grid place-items-center cursor-pointer  lg:border-very-dark-blue/20  hover:text-soft-red"><button class="cursor-pointer">Easy Sharing</button></li>
        </ul>
    </div>
</template>

<style scoped></style>
