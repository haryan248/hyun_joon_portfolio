<template>
    <div id="app">
        <Header :scrollHeight="scrollHeight" />
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
        return { scrollHeight: 0 };
    },
    mounted() {
        window.addEventListener("scroll", this.handleScroll);
    },
    destroyed() {
        window.removeEventListener("scroll");
    },
    methods: {
        handleScroll() {
            this.scrollHeight = window.scrollY;
        },
    },
};
</script>
<style scoped>
@import "./index.css";
</style>
