<template>
    <div>
        <header class="Header_Header" :class="{ Header_background: showHeader }">
            <div class="Header_content">
                <div class="Header_title">Hyun Joon's Portfolio</div>
                <div class="Header_navigation-menus">
                    <div @click="moveTotab(HeaderNavMenu.id)" class="Header_navigation-menu" v-for="(HeaderNavMenu, index) in HeaderNavMenus" :key="index">
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
            aboutLocation: 0,
            skillLocation: 0,
            projectLocation: 0,
            careerLocation: 0,
        };
    },
    computed: {},
    mounted() {
        window.addEventListener("scroll", this.handleScroll);
        this.aboutLocation = document.querySelector(".section_myinfo").offsetTop;
        this.skillLocation = document.querySelector(".section_myinfo").offsetTop - 72;
        this.projectLocation = document.querySelector(".section_project").offsetTop - 72;
        this.careerLocation = document.querySelector(".section_career").offsetTop - 72;
    },
    methods: {
        handleScroll() {
            if (window.scrollY + 72 >= document.getElementsByClassName("banner_content")[0].offsetHeight) {
                this.showHeader = true;
            } else {
                this.showHeader = false;
            }
        },
        moveTotab(id) {
            if (id === 1) {
                window.scrollTo({ top: this.aboutLocation, behavior: "smooth" });
            } else if (id === 2) {
                window.scrollTo({ top: this.skillLocation, behavior: "smooth" });
            } else if (id === 3) {
                window.scrollTo({ top: this.projectLocation, behavior: "smooth" });
            } else if (id === 4) {
                window.scrollTo({ top: this.careerLocation, behavior: "smooth" });
            }
        },
    },
};
</script>

<style scoped>
@import "./header.css";
</style>
