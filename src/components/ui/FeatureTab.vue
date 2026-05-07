<!-- FeatureTab component只放功能特色標籤，包含左側img+右側項目標題h3 + 內文p-->

<script setup lang="ts">
import { ref, computed } from "vue";
import BgBlueRect from "../ui/BgBlueRect.vue";

// 定義每一項的資料類型
interface Feature {
    id: number;
    tabName: string;
    title: string;
    description: string;
    imgSrc: string;
}
// 指定數據類型為Feature陣列，確保後續使用時的類型安全
const currentTab = ref(1);
// 將功能特色標籤的資料獨立成一個陣列，方便後續維護和擴展
const features: Feature[] = [
    {
        id:1,
        tabName: "Simple Bookmarking",
        title: "Bookmark in one click",
        description: "Organize your bookmarks however you like. Our simple drag-and-drop interface gives you complete control over how you manage your favorite sites.",
        imgSrc: "./src/assets/images/illustration-features-tab-1.svg"
    },
    {
        id:2,
        tabName: "Speedy Searching",
        title: "Intelligent search",
        description: "Our powerful search feature will help you find saved sites in no time at all. No need to trawl through all of your bookmarks.",
        imgSrc: "./src/assets/images/illustration-features-tab-2.svg"
    },
    {
        id:3,
        tabName: "Easy Sharing",
        title: "Share your bookmarks",
        description: "Easily share your bookmarks and collections with others. Create a shareable link that you can send at the click of a button.",
        imgSrc: "./src/assets/images/illustration-features-tab-3.svg"
    }
];

const activeFeature = computed(() => {
  return features.find(f => f.id === currentTab.value);
});
</script>

<template>
    <div>
        <ul class="w-[75%] mx-auto flex flex-col justify-center items-center border-y border-very-dark-blue/20
        lg:flex-row lg:border-y-0 lg:border-b lg:w-[55%]">
            <li class="w-full grid place-items-center
             lg:border-very-dark-blue/20 lg:w-1/3
             nth-2:border-y border-very-dark-blue/20
             lg:nth-2:border-y-0"
             v-for="item in features" :key="item.id">
                <button @click="currentTab = item.id"
                :class="['w-full py-4 cursor-pointer relative ',
                 currentTab === item.id ? 'text-very-dark-blue after:h-1'
                 : 'text-very-dark-blue/60 after:h-0']"

                class="hover:text-soft-red after:content-[''] after:w-[40%] after:bg-soft-red after:absolute after:bottom-0 after:left-[50%] after:transform after:translate-x-[-50%]
                lg:after:w-full">{{ item.tabName }}</button>
            </li>
        </ul>

        <div v-if="activeFeature" class="relative my-10 flex flex-col justify-center items-center
        lg:flex-row lg:my-20 md:my-10">
            <BgBlueRect class="left-[-15%] rounded-r-full top-[20%] translate-y-15 lg:translate-y-20 lg:top-[10%]"/>
            <div class="w-full flex justify-center
            lg:mb-0 lg:w-1/2">
                <img :src="activeFeature.imgSrc" :alt="activeFeature.title"  class="z-10 w-full max-w-lg"/>
            </div>
            <div class="flex flex-col justify-center items-center text-center gap-6
            sm: mt-18 md:mt-24
            lg:w-1/2 lg:text-left lg:items-start lg:pl-23"
            >
                <h2>{{ activeFeature.title }}</h2>
                <p class="lg:text-left ">{{ activeFeature.description }}</p>
                <button class="btn-blue hidden lg:block">More Info</button>
            </div>
        </div>
    </div>
</template>

<style scoped></style>
