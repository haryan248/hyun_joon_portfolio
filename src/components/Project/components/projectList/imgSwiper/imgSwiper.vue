<template>
    <Swiper :ref="'swiper-' + swiperIndex" :options="swiperOptions" @slideChangeTransitionStart="slideChangeTransitionStart('swiper-' + swiperIndex)" @slideChangeTransitionEnd="slideChangeTransitionEnd('swiper-' + swiperIndex)">
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
        swiperIndex: Number,
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
                slidesPerView: 1.5,
                spaceBetween: 11,
                centeredSlides: true,
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
            let ref = "swiper-" + this.swiperIndex;
            console.log(this.$refs[ref]);
            return this.$refs[ref];
        },
    },
    methods: {
        slideChangeTransitionStart(ref) {
            if (this.$refs[ref].activeIndex === this.imgLength + 1) {
                this.$set(this.animation, 0, true);
            } else {
                this.$set(this.animation, this.swiper.activeIndex - 1, true);
            }
        },
        slideChangeTransitionEnd(ref) {
            if (this.$refs[ref].activeIndex === this.imgLength + 1) {
                this.$set(this.animation, 0, false);
            } else {
                this.$set(this.animation, this.swiper.activeIndex - 1, false);
            }
        },
    },
};
</script>
<style scoped>
@import url("./img-swiper.css");
</style>
<style></style>
