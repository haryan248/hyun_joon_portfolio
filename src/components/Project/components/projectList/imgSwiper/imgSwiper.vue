<template>
    <Swiper ref="swiper" :slides-per-view="1" :options="swiperOptions" @slideChangeTransitionStart="slideChangeTransitionStart" @slideChangeTransitionEnd="slideChangeTransitionEnd">
        <SwiperSlide v-for="(image, index) in images" :key="index">
            <div class="swiper_wrapper">
                <div class="swiper_content">
                    <div class="swiper_background"></div>
                    <img class="swiper_img" :src="image.url" />
                </div>
            </div>
            <div class="card-text" :class="{ 'card-text-animation': animation[index] == true }">
                <h5>{{ image.title }}</h5>
            </div>
        </SwiperSlide>
        <!-- pagination -->
        <div class="swiper-pagination" slot="pagination"></div>
        <!-- navigation -->
        <div class="swiper-button-prev swiper-btn-prev" slot="button-prev"></div>
        <div class="swiper-button-next swiper-btn-next" slot="button-next"></div>
    </Swiper>
</template>
<script>
import { Swiper, SwiperSlide } from "vue-awesome-swiper";
import "swiper/css/swiper.css";
export default {
    name: "ImgSwiper",
    props: {
        images: Array,
        imgLength: Number,
    },
    components: {
        Swiper,
        SwiperSlide,
    },
    data() {
        return {
            animation: [],
            swiperOptions: {
                loop: true,
                autoplay: {
                    delay: 3000,
                    disableOnInteraction: false,
                },

                pagination: {
                    el: ".swiper-pagination",
                },
                navigation: {
                    nextEl: ".swiper-button-next",
                    prevEl: ".swiper-button-prev",
                },
            },
        };
    },
    computed: {
        swiper() {
            return this.$refs.swiper.$swiper;
        },
    },
    methods: {
        slideChangeTransitionStart() {
            if (this.swiper.activeIndex === this.imgLength + 1) {
                this.$set(this.animation, 0, true);
            } else {
                this.$set(this.animation, this.swiper.activeIndex - 1, true);
            }
        },
        slideChangeTransitionEnd() {
            if (this.swiper.activeIndex === this.imgLength + 1) {
                this.animation[0] = false;
            } else {
                this.animation[this.swiper.activeIndex - 1] = false;
            }
        },
    },
};
</script>
<style scoped>
@import url("./img-swiper.css");
</style>
