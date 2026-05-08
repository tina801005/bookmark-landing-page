<!-- DownloadCards component只放下載卡片，包含 圖片img、標題h3、內文p、 點點分隔線img、下載按鈕button -->

<script setup lang="ts">
import { ref, onMounted } from "vue";
// 定義卡片資訊的類型，包含id、圖片來源、名稱和最低版本要求
interface cardInfo {
    id: number;
    imgSrc: string;
    name: string;
    minVersion: string;
}

// 定義卡片資訊的陣列，包含每個卡片的圖片來源、名稱和最低版本要求
const cards: cardInfo[] = [
    {
        id: 1,
        imgSrc: "/src/assets/images/logo-chrome.svg",
        name: "Chrome",
        minVersion: "62"
    },
    {
        id: 2,
        imgSrc: "/src/assets/images/logo-firefox.svg",
        name: "Firefox",
        minVersion: "55"
    },
    {
        id: 3,
        imgSrc: "/src/assets/images/logo-opera.svg",
        name: "Opera",
        minVersion: "46"
    }
];

const isVisible = ref(false); // 控制動畫啟動的開關
const target = ref<HTMLElement | null>(null); // 指向父容器的 ref

onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    if (entries[0].isIntersecting) {
      isVisible.value = true;
      observer.unobserve(entries[0].target); // 跑過一次動畫就停止監測
    }
  }, { threshold: 1 }); // 當 100% 的內容出現在畫面時觸發

  if (target.value) observer.observe(target.value);
});
</script>

<template>
    <div ref="target" class="w-full flex flex-col justify-center items-center my-10 lg:flex-row lg:gap-10">
        <TransitionGroup name="drop" appear>
            <div v-for="(item, index) in cards" :key="item.id"
                v-if="isVisible"
                class="drop-card min-w-70 flex flex-col justify-center items-center p-6 my-5 rounded-2xl overflow-hidden border border-transparent shadow-xl lg:w-[20%]"
                :style="{ marginTop: index > 0 ? `${index * 40}px` : '0px',
                transitionDelay: `${index * 150}ms` }">
                <div class="flex flex-col justify-center items-center gap-4 pt-5">
                    <img :src="item.imgSrc" :alt="item.name">
                    <h3 class="text-very-dark-blue text-[clamp(1rem,1rem+1vw,1.5rem)] font-medium text-center">Add to {{item.name}}</h3>
                    <p>Minimum version {{item.minVersion}}</p>
                </div>
                <div class="w-[calc(100%+5rem)] my-5 p-1 h-1 bg-[url('/src/assets/images/bg-dots.svg')] bg-repeat-x bg-center"></div>
                <button class="w-full btn-blue">Add & Install Extension</button>
            </div>
        </TransitionGroup>
    </div>
</template>

<style scoped>
/* new */
/* 進入前的初始狀態 */
.drop-enter-from {
  opacity: 0;
  transform: translateY(-30px);
}

/* 進入過程的動畫曲線 */
.drop-enter-active {
  transition: all 0.8s cubic-bezier(0.34, 1.56, 0.64, 1); /* 加上一點點 Q 彈感 */
}

/* 進入後的最終狀態 */
.drop-enter-to {
  opacity: 1;
  transform: translateY(0);
}
/* 2 */

/* .drop-enter-from {
  opacity: 0;
  transform: translateY(-30px);
}


.drop-enter-active {
  transition: all 0.7s ease-out;
}


.drop-enter-to {
  opacity: 1;
  transform: translateY(0);
} */
/* 1 */
/* .drop-card {
  opacity: 0;
  transform: translateY(-30px);
  animation: drop-card 0.7s ease-out forwards backwards;
}

@keyframes drop-card {
  to {
    opacity: 1;
    transform: translateY(0);
  }
} */
</style>
