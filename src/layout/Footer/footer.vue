<template>
    <div>
        <footer class="footer_footer blur move_background">
            <div class="footer_wrapper">
                <div class="footer_icons">
                    <a v-for="(footer_item, index) in footerData" :href="footer_item.link" :key="index" target="_blank">
                        <div class="footer_icon-wrapper footer_bg-white" :title="footer_item.title" :style="footer_item.style">
                            <span>{{ footer_item.title }}</span>
                        </div>
                        <img class="footer_icon" :src="footer_item.url" />
                    </a>
                </div>
                <div class="footer_copyright">© 2021. Ha Hyun Joon. All rights reserved.</div>
            </div>
        </footer>
        <div @click="scrollToTop" class="scrollTo_top" :class="({ 'scroll_animation-in': scrollHeight !== 0 }, { 'scroll_animation-out': scrollHeight === 0 })">
            <img class="scrollTo_icon" :src="scrollUrl" />
        </div>
    </div>
</template>
<script>
export default {
    name: "Footer",
    props: { scrollHeight: Number },
    data() {
        return {
            scrollUrl: require("@/assets/images/footer/up-arrow.png"),
            footerData: [
                {
                    link: "https://github.com/haryan248",
                    title: "Github",
                    url: require("@/assets/images/footer/github.png"),
                },
                {
                    link: "https://www.instagram.com/h__.__joon/",
                    title: "Instagram",
                    url: require("@/assets/images/footer/instagram.png"),
                },
                {
                    link: "mailto:haryan96@gmail.com",
                    title: "Mail",
                    url: require("@/assets/images/footer/email.png"),
                },
            ],
        };
    },
    methods: {
        scrollToTop() {
            window.scrollTo({ top: 0, behavior: "smooth" });
        },
    },
};
</script>

<style scoped>
@import "./footer.css";
</style>
