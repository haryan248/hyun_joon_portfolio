<template>
    <div :class="'project_wrapper_' + index">
        <div class="project_container" :class="computedClass">
            <div v-if="index % 2 === 0" class="project_img">
                <ImgSwiper :images="projects.images" :swiperIndex="index" />
            </div>
            <div class="project_intro">
                <div class="project_intro_title">
                    <span class="highlight">{{ project_index }}</span> {{ projects.title }}
                </div>
                <div class="project_intro_text">
                    <div class="project_intro-description" v-html="projects.description"></div>
                    <div class="project_description" v-for="(project_item, index) in projects" :key="index">
                        <div v-if="project_item.label" class="projects_label">{{ project_item.label }}</div>
                        <div v-if="project_item.value" class="projects_value">{{ project_item.value }}</div>
                    </div>
                    <div class="project_intro_button_box">
                        <a v-if="projects.youtube" class="project_intro_button" :href="projects.youtube" target="_blank"><div>YouTube 보기</div></a>
                        <a class="project_intro_button" :href="projects.github" target="_blank">Github 보기</a>
                    </div>
                </div>
            </div>
            <div v-if="index % 2 !== 0" class="project_img">
                <ImgSwiper :images="projects.images" />
            </div>
        </div>
    </div>
</template>
<script>
import ImgSwiper from "./imgSwiper/imgSwiper.vue";

export default {
    name: "ProjectList",
    props: {
        projects: Object,
        scrollHeight: Number,
        index: Number,
    },
    components: {
        ImgSwiper,
    },
    data() {
        return {
            currentScroll: false,
            project_index: 0,
            project_container: "",
            project_element: document.getElementsByClassName(`project_wrapper_${this.index}`),
        };
    },
    computed: {
        computedClass() {
            if (this.checkHeight) {
                return "stagger-item";
            } else {
                return "stagger-item-out";
            }
        },
        checkHeight() {
            if (this.scrollHeight >= this.project_element[0]?.offsetTop - 400) {
                return true;
            }
            return false;
        },
    },
    mounted() {
        this.project_index = this.index + 1 < 10 ? "0" + (this.index + 1) : this.index + 1;
    },
};
</script>
<style scoped>
@import url("./project-list.css");
</style>
