<!-- FAQ Toggle component包含問題p、小箭頭img、答案p -->

<script setup lang="ts">
import { ref } from "vue";

interface fqaItem {
    id:number;
    question: string;
    answer: string;
    // 這裡可以添加一個屬性來控制該項是否展開
    isOpen: boolean;
}

const fqaItems = ref<fqaItem[]>([
    {
        id: 1,
        question:"What is Bookmark?",
        answer: "Lorem ipsum dolor sit abet, consectetur adipiscing elit. Fusce tincidunt justo eget ultricies fringilla. Phasellus blandit ipsum quis quam ornare mattis.",
        isOpen: false
    },
    {
        id: 2,
        question:"How can I request a new browser?",
        answer: "Vivamus luctus eros aliquet convallis ultricies. Mauris augue massa, ultricies non ligula.Suspendisse imperdiet. Vivamus luctus eros aliquet convallis ultricies. Mauris augue massa,ultricies non ligula. Suspendisse imperdie tVivamus luctus eros aliquet convallis ultricies.Mauris augue massa, ultricies non ligula. Suspendisse imperdiet.",
        isOpen: false
    },
    {
        id: 3,
        question:"Is there a mobile app?",
        answer: "Sed consectetur quam id neque fermentum accumsan. Praesent luctus vestibulum dolor, ut condimentumurna vulputate eget. Cras in ligula quis est pharetra mattis sit amet pharetra purus. Sedsollicitudin ex et ultricies bibendum.",
        isOpen: false
    },
    {
        id: 4,
        question:"What about other Chromium browsers?",
        answer: "Integer condimentum ipsum id imperdiet finibus. Vivamus in placerat mi, at euismod dui. Aliquam vitae neque eget nisl gravida pellentesque non ut velit.",
        isOpen: false
    }
]);

const toggleItem = (targetItem: fqaItem) => {
  fqaItems.value.forEach((item) => {
    // 如果不是當前點擊的項目，就關閉它
    if (item.id !== targetItem.id) {
      item.isOpen = false;
    }
  });
  // 切換當前項目的開關
  targetItem.isOpen = !targetItem.isOpen;
};
</script>

<template>
    <div class="w-[85%] flex flex-col justify-center items-center lg:w-[36.5%]">
        <ul class="w-full lg:border-t lg:border-very-dark-blue/30">
            <li v-for="item in fqaItems" :key="item.id"
                class="w-full flex flex-col border-b border-very-dark-blue/30 list-none">

                <button @click="toggleItem(item)"
                        :id="`faq-btn-${item.id}`"
                        :aria-expanded="item.isOpen"
                        :aria-controls="`faq-panel-${item.id}`"
                        class="group w-full flex justify-between items-center cursor-pointer py-6 text-very-dark-blue hover:text-soft-red transition-colors focus-button">
                    <span class="text-start">{{ item.question }}</span>
                    <span>
                        <img src="/src/assets/images/icon-arrow.svg" alt="" aria-hidden="true"
                             class="transition-all duration-300"
                             :class="item.isOpen ? 'rotate-180 arrow-red' : 'rotate-0'">
                    </span>
                </button>

                <div :id="`faq-panel-${item.id}`" class="overflow-hidden transition-all duration-300"
                     :class="item.isOpen ? 'max-h-96 pb-6' : 'max-h-0'" role="region" :aria-labelledby="`faq-btn-${item.id}`">
                    <p class="text-start text-very-dark-blue/70 px-0 lg:text-base/8">
                        {{ item.answer }}
                    </p>
                </div>
            </li>
        </ul>
        <div class="w-full grid place-items-center lg:w-[28%] mt-10">
            <button class="btn-blue focus-button">More Info</button>
        </div>
    </div>
</template>

<style scoped>
.arrow-red {
  filter: invert(19%) sepia(96%) saturate(7480%) hue-rotate(360deg) brightness(105%) contrast(105%);
}
</style>
