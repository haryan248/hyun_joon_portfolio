<template>
    <div>
        <header class="Header_Header" :class="{ Header_background: showHeader }">
            <div class="Header_content">
                <div class="Header_title">Hyun Joon's Portfolio</div>
                <div class="Header_navigation-menus">
                    <div class="Header_navigation-menu" v-for="(HeaderNavMenu, index) in HeaderNavMenus" :key="index">
                        {{ HeaderNavMenu.name }}
                    </div>
                </div>
            </div>
        </header>
    </div>
</template>
<script>
export default {
    name: "Header",
    data() {
        return {
            HeaderNavMenus: [
                { id: 1, name: "About me" },
                { id: 2, name: "Skills" },
                { id: 3, name: "Projects" },
                { id: 4, name: "Career" },
            ],
            showHeader: false,
        };
    },
    computed: {},
    mounted() {
        window.addEventListener("scroll", this.handleScroll);
    },
    methods: {
        handleScroll() {
            // if (this.showHeader) {
            //     this.modalCurPosition = this.modalObject.scrollTop;
            // } else {
            //     this.curPosition = window.scrollY;
            // }
            if (window.scrollY + 72 >= document.getElementsByClassName("banner_content")[0].offsetHeight) {
                this.showHeader = true;
            } else {
                this.showHeader = false;
            }
            console.log(window.scrollY);
            console.log();
        },
    },
};
</script>

<style scoped>
@import "./header.css";
</style>
