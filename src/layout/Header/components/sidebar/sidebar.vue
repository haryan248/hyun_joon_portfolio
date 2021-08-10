<template>
    <section>
        <div :class="{ 'header_hamburger-wrapper': checkWidth }" @click="toggleSidebar">
            <img :src="hamburgerMenu" />
        </div>
        <transition>
            <div v-if="sidebarStatus" class="modal_overlay" @click="toggleSidebar">
                <div class="dialog" @click.stop>
                    <div class="side_bar-wrapper">
                        <div class="side_bar-close" @click="toggleSidebar">
                            <img :src="closeButton" />
                        </div>
                        <div class="side_bar-menus">
                            <div class="menu_title"><p>HYUNJOON</p></div>
                            <div class="side_bar-menu">
                                <div @click="moveTotab(HeaderNavMenu.id)" class="header_navigation-mobile-menu" v-for="(HeaderNavMenu, index) in HeaderNavMenus" :key="index">
                                    {{ HeaderNavMenu.name }}
                                </div>
                            </div>
                        </div>
                        <div class="side_bar-link">
                            <a v-for="(link_item, index) in linkData" :href="link_item.link" :key="index" target="_blank">
                                <div class="link_icon-wrapper" :title="link_item.title">
                                    <div class="link_icon-container">
                                        <img class="link_icon" :src="link_item.url" />
                                        <div class="icon_title">{{ link_item.title }}</div>
                                    </div>
                                </div>
                            </a>
                        </div>
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
            linkData: [
                {
                    link: "https://github.com/haryan248",
                    title: "GitHub",
                    url: require("@/assets/images/header/github.png"),
                },
                {
                    link: "https://www.instagram.com/h__.__joon/",
                    title: "Instagram",
                    url: require("@/assets/images/header/instagram.png"),
                },
                {
                    link: "mailto:haryan96@gmail.com",
                    title: "Mail",
                    url: require("@/assets/images/header/email.png"),
                },
            ],
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
