<!-- FAQSection component只放常見問題內容，包含 次標題h2、內文p、FAQ toggle -->

<script setup>
import FQAToggle from "../ui/FQAToggle.vue";
</script>

<template>
    <section class="w-full my-16 lg:my-30">
        <div class="flex flex-col justify-center items-center">
            <div class="flex flex-col justify-center items-center gap-6">
                <h2 class="text-center">Frequently Asked Questions</h2>
                <p class="max-w-md">Here are some of our FAQs. If you have any other questions you’d like
  answered please feel free to email us.</p>
            </div>
            <FQAToggle class="my-6"/>
        </div>
    </section>
</template>

<style scoped></style>
