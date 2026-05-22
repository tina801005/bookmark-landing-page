<script setup lang="ts">
import TheHeader from "./components/layout/TheHeader.vue";
import HeroSection from "./components/layout/HeroSection.vue";
import FeatureSection from "./components/layout/FeatureSection.vue";
import DownloadSection from "./components/layout/DownloadSection.vue";
import FAQSection from "./components/layout/FAQSection.vue";
import TheFooter from "./components/layout/TheFooter.vue";

</script>

<template>
    <main class="main font-base">
        <TheHeader />
        <div class="p-10 lg:p-20">
            <HeroSection />
            <FeatureSection />
            <DownloadSection />
            <FAQSection />
        </div>

        <TheFooter />
    </main>

</template>


<style scoped></style>
