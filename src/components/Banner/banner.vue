<template>
    <div class="section_banner">
        <div class="banner_content">
            <div class="banner_title">
                <div class="banner_animaiton-left">WELCOME!</div>
                <div class="banner_animaiton-right">HYUNJOON'S PORTFOLIO</div>
            </div>
            <div class="banner_more-button" @click="clickMoreButton"></div>
            <div class="bannerDesign_wrapper">
                <div v-for="(designElements, key) in designItem" :key="key">
                    <div v-for="(designElement, index) in designElements" :key="`${key}-${index}`">
                        <div :class="`${key} ${key}_${designElement.index}`" :style="designElement.style"></div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: "Banner",
    data() {
        return {
            designItem: {
                circle: [
                    { index: 1, style: "" },
                    { index: 2, style: "" },
                    { index: 3, style: "" },
                    { index: 4, style: "" },
                    { index: 5, style: "" },
                ],

                pill: [
                    { index: 1, style: "" },
                    { index: 2, style: "" },
                    { index: 3, style: "" },
                    { index: 4, style: "" },
                ],
            },
        };
    },
    mounted() {
        Object.values(this.designItem).forEach((value) => {
            value.forEach((element) => {
                let random = Math.floor(Math.random() * 5 + 2);
                element.style = "animationDuration: " + random + "s";
                return element.style;
            });
        });
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
