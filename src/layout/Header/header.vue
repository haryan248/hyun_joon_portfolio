<template>
    <div>
        <header class="section_header" :class="[{ header_background: checkHeight || checkWidth }]">
            <div class="header_content">
                <div class="header_title">Hyun Joon</div>
                <Sidebar ref="sidebar" v-if="checkWidth" :HeaderNavMenus="HeaderNavMenus" :checkWidth="checkWidth" @moveTotab="moveTotab" />
                <div v-else class="header_navigation-menus">
                    <div @click="moveTotab(HeaderNavMenu.id)" class="header_navigation-menu" v-for="(HeaderNavMenu, index) in HeaderNavMenus" :key="index">
                        {{ HeaderNavMenu.name }}
                    </div>
                </div>
            </div>
        </header>
    </div>
</template>
<script>
import Sidebar from "./components/sidebar/sidebar.vue";

export default {
    name: "Header",
    props: {
        scrollHeight: Number,
        bodyWidth: Number,
    },
    components: { Sidebar },
    data() {
        return {
            HeaderNavMenus: [
                { id: 1, name: "About me" },
                { id: 2, name: "Skills" },
                { id: 3, name: "Projects" },
                { id: 4, name: "Career" },
            ],
            headerElement: document.getElementsByClassName("section_header"),
            aboutElement: document.getElementsByClassName("section_myinfo"),
            aboutLocation: 0,
            skillLocation: 0,
            projectLocation: 0,
            careerLocation: 0,
        };
    },
    computed: {
        checkHeight() {
            if (this.scrollHeight + this.headerElement[0]?.offsetHeight > this.aboutElement[0]?.offsetTop - 10) {
                return true;
            } else {
                return false;
            }
        },
        checkWidth() {
            if (this.bodyWidth < 767) {
                return true;
            } else return false;
        },
    },
    mounted() {
        this.setLocation();
    },
    methods: {
        setLocation() {
            this.aboutLocation = document.querySelector(".section_myinfo").offsetTop - this.headerElement[0].offsetHeight;
            this.skillLocation = document.querySelector(".section_skill").offsetTop - this.headerElement[0].offsetHeight;
            this.projectLocation = document.querySelector(".section_project").offsetTop - this.headerElement[0].offsetHeight;
            this.careerLocation = document.querySelector(".section_career").offsetTop - this.headerElement[0].offsetHeight;
        },
        moveTotab(id, sidebarStatus) {
            if (id === 1) {
                window.scrollTo({ top: document.querySelector(".section_myinfo").offsetTop - this.headerElement[0].offsetHeight, behavior: "smooth" });
            } else if (id === 2) {
                window.scrollTo({ top: document.querySelector(".section_skill").offsetTop - this.headerElement[0].offsetHeight, behavior: "smooth" });
            } else if (id === 3) {
                window.scrollTo({ top: document.querySelector(".section_project").offsetTop - this.headerElement[0].offsetHeight, behavior: "smooth" });
            } else if (id === 4) {
                window.scrollTo({ top: document.querySelector(".section_career").offsetTop - this.headerElement[0].offsetHeight, behavior: "smooth" });
            }
            if (sidebarStatus) this.$refs.sidebar.toggleSidebar();
        },
    },
};
</script>

<style scoped>
@import "./header.css";
</style>
