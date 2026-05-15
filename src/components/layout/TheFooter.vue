<!-- TheFooter component只放頁面底部內容，包含 次標題h2、內文p、input field(email輸入框)、send button、footer-nav(logo+nav+social media links) -->

<script setup lang="ts">
import { ref, watch } from "vue";
// 第一部分主要邏輯 1.email輸入框驗證 2.輸入錯誤出現錯誤提示(錯誤提示包含input父元素div的背景色變紅色+span提示文字+error icon出現)

// email驗證的正則表達式，確保輸入的內容符合基本的email格式
const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
// 定義一個ref來存儲用戶輸入的email地址
const email = ref("");
// 定義一個ref來控制錯誤提示的顯示
const showError = ref(false);

// 即時驗證 email 輸入
watch(email, (newEmail) => {
    if (newEmail.trim() === "") {
        showError.value = false; // 空輸入時不顯示錯誤
    } else {
        showError.value = !emailRegex.test(newEmail);
    }
});

// 定義一個方法來處理表單提交，進行email驗證
const handleSubmit = () => {
    if (!emailRegex.test(email.value)) {
        showError.value = true; // 如果驗證失敗，顯示錯誤提示
    } else {
        showError.value = false; // 如果驗證成功，隱藏錯誤提示
        // 這裡可以添加提交表單的邏輯，例如發送API請求等
    }
};

</script>

<template>
    <!-- 第一部分section -->
    <footer class="w-full">
        <section class="bg-soft-blue w-full flex flex-col justify-center items-center text-center py-16 px-10">
            <div class="flex flex-col gap-10 lg:w-[40%]">
                <div class="flex flex-col gap-5 lg:gap-10">
                    <p class="text-white-gray tracking-[0.5rem] uppercase">35,000+ already joined</p>
                    <h2 class="text-white-gray ">Stay up-to-date with what we’re doing</h2>
                </div>
                <div class="flex flex-col justify-center items-center gap-5 lg:flex-row lg:justify-between" >
                    <div class="w-full rounded-lg p-1 relative
                     lg:w-full"
                         :class="showError ? 'bg-soft-red' : 'bg-transparent'">
                        <input type="email" placeholder="Enter your email address"
                    class="w-full bg-white-gray p-4 rounded-lg"
                    v-model="email"
                    :class="showError ? 'border border-soft-red' : ''"
                    aria-label="Email address"/>
                        <span v-show="showError"
                        class="w-full block p-3 bg-soft-red rounded-lg text-left text-white-gray text-sm overflow-hidden transition-all duration-300"
                        :style="{ maxHeight: showError ? '100px' : '0px' }"><i>Whoops, make sure it's a email</i></span>

                        <div v-if="showError"
                         class="w-auto h-auto absolute flex items-center justify-center
                        top-0 right-0 translate-y-full -translate-x-full">
                            <img src="/src/assets/images/icon-error.svg" alt="Error icon" />
                        </div>
                    </div>
                    <button class="w-full text-center bg-soft-red text-white-gray p-4 rounded-lg cursor-pointer border border-transparent
                     lg:w-1/3
                     hover:bg-white-gray hover:border-2 hover:border-soft-red hover:text-soft-red"
                     @click="handleSubmit">Contact Us</button>
                </div>
            </div>
        </section>

        <!-- 第二部分footer-nav -->
        <nav class="bg-very-dark-blue w-full py-6" aria-label="footer navigation">
            <!-- <div class="debug w-full flex flex-col justify-center items-center p-10
        lg:flex-row lg:justify-between lg:p-0 lg:mx-auto lg:max-w-6xl lg:gap-6"> -->
            <div class="w-full grid gap-5 p-10 lg:grid-cols-[auto_1fr_auto] lg:items-center lg:p-0 lg:mx-auto lg:max-w-6xl">

                    <div class="grid place-items-center mb-5
                    lg:mb-0 lg:mr-10">
                        <img src="/src/assets/images/logo-bookmark-footer.svg" alt="bookmark logo" />
                    </div>
                    <ul class="flex flex-col text-white-gray uppercase tracking-[0.1rem] gap-5 text-center
                    lg:flex-row lg:justify-start ">
                        <li class="cursor-pointer hover:text-soft-red">Features</li>
                        <li class="cursor-pointer hover:text-soft-red">Pricing</li>
                        <li class="cursor-pointer hover:text-soft-red">Contact</li>
                    </ul>
                    <ul class="flex justify-center items-center gap-10 mt-5 lg:mt-0 ">
                        <li class="social-icon">
                            <img src="/src/assets/images/icon-facebook.svg" alt="Facebook">
                        </li>
                        <li class="social-icon">
                            <img src="/src/assets/images/icon-twitter.svg" alt="Twitter">
                        </li>
                    </ul>
            </div>

        </nav>
    </footer>

    <!-- 這個footer總共會有兩塊
    1.section
        只放p,h2和input+button
    2.footer-nav
        放logo、nav、social media links -->
</template>

<style scoped>
.social-icon:hover{
        filter: brightness(0) saturate(100%) invert(53%) sepia(31%) saturate(7466%) hue-rotate(330deg) brightness(106%) contrast(100%);
        cursor: pointer;
}
</style>
