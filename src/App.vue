<template>
    <div id="app">
        <Header />
        <Maincontent />
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
};
</script>
<style scoped>
@import "./index.css";
</style>
