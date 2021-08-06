<template>
    <div class="section_banner">
        <div class="banner_content">
            <div class="banner_title">
                <div class="banner_animaiton-left">WELCOME!</div>
                <div class="banner_animaiton-right">HYUNJOON'S PORTFOLIO</div>
            </div>
            <div class="banner_more-button" @click="clickMoreButton"></div>
            <div class="circle_wrapper">
                <div class="circle circle_1"></div>
                <div class="circle circle_2"></div>
                <div class="circle circle_3"></div>
                <div class="circle circle_4"></div>
                <div class="circle circle_5"></div>
                <div class="circle circle_6"></div>
                <div class="circle circle_7"></div>
                <div class="circle circle_8"></div>
                <div class="circle circle_9"></div>
            </div>
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
