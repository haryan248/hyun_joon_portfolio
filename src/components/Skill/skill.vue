<template>
    <section class="section_skill background_black">
        <div class="skill_content" :class="computedClass">
            <div class="skill_section_title_wrap">
                <span class="section_title border_bottom">SKILLS</span>
            </div>
        </div>
        <div class="skill_container" :class="[{ 'stagger-item': checkHeight }, { 'stagger-item-out': !checkHeight }]" v-for="(skill, index) in skills" :key="index">
            <div class="status_title ">{{ index }}</div>
            <div class="status_content" v-for="skill_item in skill" :key="skill_item.label">
                <div class="status_bar-title">{{ skill_item.label }}</div>
                <div class="status_bar-item">
                    <div class="status_bar-percent" :class="getClass(skill_item.value)" :style="'animationDuration:' + durationList[skill_item.id] + 's'">{{ skill_item.value }}%</div>
                </div>
            </div>
        </div>
    </section>
</template>
<script>
export default {
    name: "Skill",
    props: { scrollHeight: Number },
    data() {
        return {
            durationList: [],
            skillElement: document.getElementsByClassName("section_skill"),
            skills: {
                FrontEnd: [
                    { id: 0, label: "HTML5", value: "75" },
                    { id: 1, label: "CSS3", value: "70" },
                    { id: 2, label: "Javascript", value: "65" },
                    { id: 3, label: "Vue.js", value: "75" },
                    { id: 4, label: "React.js", value: "50" },
                ],
                BackEnd: [
                    { id: 5, label: "Django", value: "50" },
                    { id: 6, label: "Spring", value: "20" },
                ],
                ConfigurationManagement: [{ id: 7, label: "GitHub", value: "70" }],
                Communication: [
                    { id: 8, label: "Slack", value: "80" },
                    { id: 9, label: "Figma", value: "80" },
                    { id: 10, label: "Jira", value: "70" },
                ],
            },
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
            if (this.scrollHeight >= this.skillElement[0]?.offsetTop - 400) {
                return true;
            }
            return false;
        },
    },
    mounted() {
        this.setAnimationStyle();
    },
    methods: {
        getClass(value) {
            if (this.checkHeight) return ["percent_animation-" + value, "percent_opacity_zero"];
            else return "percent_animation-" + value + "-out";
        },
        setAnimationStyle() {
            let duration = 0.7;
            for (let i = 0; i < this.skills.FrontEnd.length + this.skills.BackEnd.length + this.skills.ConfigurationManagement.length + this.skills.Communication.length; i++) {
                duration += 0.3;
                this.durationList.push(duration);
            }
        },
    },
};
</script>
<style scoped>
@import url("./skill.css");
</style>
