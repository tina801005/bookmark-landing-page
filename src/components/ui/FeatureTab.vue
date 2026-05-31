<!-- FeatureTab component只放功能特色標籤，包含左側img+右側項目標題h3 + 內文p-->

<script setup lang="ts">
import { ref, computed } from "vue";
import BgBlueRect from "../ui/BgBlueRect.vue";

// import導入圖片資源，這裡使用相對路徑來確保在構建過程中能正確解析
import featuresTab1Url from "../../assets/images/illustration-features-tab-1.svg";
import featuresTab2Url from "../../assets/images/illustration-features-tab-2.svg";
import featuresTab3Url from "../../assets/images/illustration-features-tab-3.svg";

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
        imgSrc: featuresTab1Url
    },
    {
        id:2,
        tabName: "Speedy Searching",
        title: "Intelligent search",
        description: "Our powerful search feature will help you find saved sites in no time at all. No need to trawl through all of your bookmarks.",
        imgSrc: featuresTab2Url
    },
    {
        id:3,
        tabName: "Easy Sharing",
        title: "Share your bookmarks",
        description: "Easily share your bookmarks and collections with others. Create a shareable link that you can send at the click of a button.",
        imgSrc: featuresTab3Url
    }
];

const activeFeature = computed(() => {
  return features.find(f => f.id === currentTab.value);
});

const handleTabKeydown = (event: KeyboardEvent, itemId: number) => {
  const currentIndex = features.findIndex((feature) => feature.id === itemId);
  if (currentIndex === -1) return;

  let nextIndex = currentIndex;
  if (event.key === 'ArrowRight') {
    nextIndex = (currentIndex + 1) % features.length;
  } else if (event.key === 'ArrowLeft') {
    nextIndex = (currentIndex - 1 + features.length) % features.length;
  } else {
    return;
  }

  currentTab.value = features[nextIndex].id;
  const tabs = (event.currentTarget as HTMLElement).closest('ul')?.querySelectorAll('[role="tab"]');
  if (tabs && tabs[nextIndex] instanceof HTMLElement) {
    tabs[nextIndex].focus();
  }
  event.preventDefault();
};
</script>

<template>
    <div class="mt-15">
        <ul class="w-[75%] mx-auto flex flex-col justify-center items-center border-y border-very-dark-blue/20
        lg:flex-row lg:border-y-0 lg:border-b lg:w-[55%]" role="tablist" aria-label="Feature tabs">
                     <li class="w-full grid place-items-center
             lg:border-very-dark-blue/20 lg:w-1/3
             nth-2:border-y border-very-dark-blue/20
             lg:nth-2:border-y-0"
             v-for="item in features" :key="item.id">
                     <button @click="currentTab = item.id"
                     @keydown="handleTabKeydown($event, item.id)"
                     :id="`tab-${item.id}`"
                     :aria-controls="`feature-panel-${item.id}`"
                     :aria-selected="currentTab === item.id"
                     role="tab"
                     class="w-full py-4 cursor-pointer relative hover:text-soft-red after:content-[''] after:w-[40%] after:bg-soft-red after:absolute after:bottom-0 after:left-[50%] after:transform after:translate-x-[-50%] lg:after:w-full focus-button"
                     :class="currentTab === item.id ? 'text-very-dark-blue after:h-1' : 'text-very-dark-blue/60 after:h-0'">
                     {{ item.tabName }}</button>
            </li>
        </ul>

        <div v-if="activeFeature" :id="`feature-panel-${currentTab}`" class="relative my-10 flex flex-col justify-center items-center
        lg:flex-row lg:my-20 md:my-10">
            <BgBlueRect class="rounded-r-full bottom-45 -left-10
            md:left-[-20%]
            lg:-bottom-10 lg:left-[-20%]
            xl:left-[-20%]
            "/>
            <div class="w-[80%] flex justify-center
            lg:mb-0 lg:w-auto">
                <img :src="activeFeature.imgSrc" :alt="activeFeature.title"  class="z-10 w-full max-w-lg"/>
            </div>
            <div class="flex flex-col justify-center items-center text-center gap-6
            sm: mt-18 md:mt-24
            lg:w-1/2 lg:text-left lg:items-start lg:pl-23"
            role="tabpanel" :aria-labelledby="`tab-${currentTab}`" tabindex="0"
            >
                <h2>{{ activeFeature.title }}</h2>
                <p class="max-w-md lg:text-left ">{{ activeFeature.description }}</p>
                <button class="btn-blue hidden lg:block focus-button">More Info</button>
            </div>
        </div>
    </div>
</template>

<style scoped></style>
