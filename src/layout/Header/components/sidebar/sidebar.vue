<template>
    <section>
        <div :class="{ 'header_hamburger-wrapper': checkWidth }" @click="toggleSidebar">
            <img :src="hamburgerMenu" />
        </div>
        <transition>
            <div v-if="sidebarStatus" class="modal_overlay" @click="toggleSidebar">
                <div class="dialog" @click.stop>
                    <div class="side_bar-wrapper">
                        <section class="side_bar-close" @click="toggleSidebar">
                            <img :src="closeButton" />
                        </section>
                        <section class="side_bar-menus">
                            <div class="menu_title"><p>HyunJoon Portfolio</p></div>
                            <div class="side_bar-menu">
                                <div @click="moveTotab(HeaderNavMenu.id)" class="header_navigation-mobile-menu" v-for="(HeaderNavMenu, index) in HeaderNavMenus" :key="index">
                                    {{ HeaderNavMenu.name }}
                                </div>
                            </div>
                        </section>
                    </div>
                </div>
            </div>
        </transition>
    </section>
</template>
<script>
export default {
    name: "Sidebar",
    data() {
        return {
            sidebarStatus: false,
            closeButton: require("@/assets/images/header/cancel.png"),
            hamburgerMenu: require("@/assets/images/header/hamburger_button_menu_icon.png"),
        };
    },
    props: { HeaderNavMenus: Array, checkWidth: Boolean },
    methods: {
        toggleSidebar() {
            this.sidebarStatus = !this.sidebarStatus;
            if (this.sidebarStatus) {
                document.body.style.setProperty("overflow", "hidden");
            } else {
                document.body.style.removeProperty("overflow");
            }
        },
        moveTotab(id) {
            this.$emit("moveTotab", id, this.sidebarStatus);
        },
    },
};
</script>
<style scoped>
@import "./sidebar.css";
</style>
