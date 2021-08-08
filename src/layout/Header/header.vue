<template>
    <div>
        <header class="section_header" :class="[{ header_background: checkHeight || checkWidth }]">
            <div class="header_content">
                <div class="header_title">Hyun Joon</div>
                <div v-if="checkWidth" :class="{ 'header_hamburger-wrapper': checkWidth }" @click="toggleSidebar">
                    <img :src="hamburgerMenu" />
                </div>
                <div v-if="!checkWidth" class="header_navigation-menus">
                    <div @click="moveTotab(HeaderNavMenu.id)" class="header_navigation-menu" v-for="(HeaderNavMenu, index) in HeaderNavMenus" :key="index">
                        {{ HeaderNavMenu.name }}
                    </div>
                </div>
                <div v-else>
                    <transition>
                        <div v-if="sidebarStatus" class="modal_overlay" @click="toggleSidebar">
                            <div class="dialog" @click.stop>
                                <div class="side-panel-wrapper">
                                    <section class="side-panel-close" @click="toggleSidebar">
                                        <img :src="closeButton" />
                                    </section>
                                    <section class="gnb-side">
                                        <div class="mobile-side-message"><p>HyunJoon Portfolio</p></div>
                                        <div class="mobile-side-menu">
                                            <div @click="moveTotab(HeaderNavMenu.id)" class="header_navigation-mobile-menu" v-for="(HeaderNavMenu, index) in HeaderNavMenus" :key="index">
                                                {{ HeaderNavMenu.name }}
                                            </div>
                                        </div>
                                    </section>
                                </div>
                            </div>
                        </div>
                    </transition>
                </div>
            </div>
        </header>
    </div>
</template>
<script>
export default {
    name: "Header",
    props: {
        scrollHeight: Number,
        bodyWidth: Number,
    },
    data() {
        return {
            HeaderNavMenus: [
                { id: 1, name: "About me" },
                { id: 2, name: "Skills" },
                { id: 3, name: "Projects" },
                { id: 4, name: "Career" },
            ],
            hamburgerMenu: require("@/assets/images/header/hamburger_button_menu_icon.png"),
            closeButton: require("@/assets/images/header/cancel.png"),
            headerElement: document.getElementsByClassName("section_header"),
            aboutElement: document.getElementsByClassName("section_myinfo"),
            showHeader: false,
            aboutLocation: 0,
            skillLocation: 0,
            projectLocation: 0,
            careerLocation: 0,
            sidebarStatus: false,
        };
    },
    computed: {
        checkHeight() {
            if (this.scrollHeight + this.headerElement[0]?.offsetHeight >= this.aboutElement[0]?.offsetTop) {
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
            this.aboutLocation = document.querySelector(".section_myinfo").offsetTop;
            this.skillLocation = document.querySelector(".section_skill").offsetTop;
            this.projectLocation = document.querySelector(".section_project").offsetTop;
            this.careerLocation = document.querySelector(".section_career").offsetTop;
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
            this.toggleSidebar();
        },
        toggleSidebar() {
            this.sidebarStatus = !this.sidebarStatus;
            if (this.sidebarStatus) {
                document.body.style.setProperty("overflow", "hidden");
            } else {
                document.body.style.removeProperty("overflow");
            }
        },
    },
};
</script>

<style scoped>
@import "./header.css";
</style>
