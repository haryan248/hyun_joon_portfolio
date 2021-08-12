<template>
    <div ref="app" id="app">
        <Header :scrollHeight="scrollHeight" :checkWidth="checkWidth" />
        <Maincontent :scrollHeight="scrollHeight" :checkWidth="checkWidth" />
        <Footer :scrollHeight="scrollHeight" />
    </div>
</template>

<script>
import Header from "./layout/Header/header.vue";
import Footer from "./layout/Footer/footer.vue";
import Maincontent from "./pages/Main-content/maincontent.vue";

export default {
    name: "App",
    components: { Header, Footer, Maincontent },
    data() {
        return { scrollHeight: 0, checkWidth: true };
    },
    mounted() {
        window.addEventListener("scroll", this.handleScroll);
        window.addEventListener("resize", this.handleResize);
        this.handleResize();
    },
    beforeDestroy() {
        window.removeEventListener("scroll", this.handleScroll);
        window.removeEventListener("resize", this.handleResize);
    },
    methods: {
        handleScroll() {
            this.scrollHeight = window.scrollY;
        },
        handleResize() {
            if (window.innerWidth < 767) {
                this.checkWidth = true;
            } else this.checkWidth = false;
        },
    },
};
</script>
<style scoped>
@import "./index.css";
</style>
