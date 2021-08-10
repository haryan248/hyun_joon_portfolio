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
        checkWidth: Boolean,
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
            skillElement: document.querySelector(".section_skill"),
            projectElement: document.querySelector(".section_project"),
            careerElement: document.querySelector(".section_career"),
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
    },
    mounted() {},
    methods: {
        setLocation(id) {
            if (id === 1) {
                return this.aboutElement.offsetTop - this.headerElement[0].offsetHeight;
            } else if (id === 2) {
                return this.skillElement.offsetTop - this.headerElement[0].offsetHeight;
            } else if (id === 3) {
                return this.projectElement.offsetTop - this.headerElement[0].offsetHeight;
            } else if (id === 4) {
                return this.careerElement.offsetTop - this.headerElement[0].offsetHeight;
            }
        },
        moveTotab(id, sidebarStatus) {
            if (sidebarStatus) this.$refs.sidebar.toggleSidebar();
            window.scrollTo({ top: this.setLocation(id), behavior: "smooth" });
        },
    },
};
</script>

<style scoped>
@import "./header.css";
</style>
