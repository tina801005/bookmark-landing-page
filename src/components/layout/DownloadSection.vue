<!-- DownloadSection component只放下載按鈕和相關資訊，內容物有 h2、p、DownloadCards -->

<script setup>
import DownloadCards from "../ui/DownloadCards.vue";
</script>

<template>
    <section class="w-full my-16 lg:my-30">
        <div class="w-full flex flex-col justify-center items-center">
            <div class="flex flex-col justify-center items-center gap-6">
                <h2>Download the extension</h2>
                <p >We’ve got more browsers in the pipeline. Please do let us know if you’ve got a favorite you’d like us to prioritize.</p>
            </div>
            <DownloadCards />
        </div>
    </section>

</template>

<style scoped></style>
