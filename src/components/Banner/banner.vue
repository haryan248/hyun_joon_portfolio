<template>
    <div class="section_banner">
        <div class="banner_content">
            <div class="banner_title">WELCOME!<br />HYUNJOON'S PORTFOLIO</div>
            <div class="banner_more-button" @click="clickMoreButton"></div>
        </div>
    </div>
</template>
<script>
export default {
    name: "Banner",
    data() {
        return {};
    },
    methods: {
        clickMoreButton() {
            window.scrollTo({ top: document.querySelector(".section_myinfo").offsetTop, behavior: "smooth" });
        },
    },
};
</script>
<style scoped>
@import url("./banner.css");
</style>
