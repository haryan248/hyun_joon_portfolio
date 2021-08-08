<template>
    <div ref="app" id="app">
        <Header :scrollHeight="scrollHeight" :bodyWidth="bodyWidth" />
        <Maincontent :scrollHeight="scrollHeight" />
        <Footer />
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
        return { scrollHeight: 0, bodyWidth: 0 };
    },
    mounted() {
        window.addEventListener("scroll", this.handleScroll);
        window.addEventListener("resize", this.handleResize);
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
            this.bodyWidth = window.innerWidth;
        },
    },
};
</script>
<style scoped>
@import "./index.css";
</style>
