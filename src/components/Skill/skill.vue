<template>
    <section class="section_skill">
        <div class="skill_content" :class="[{ 'stagger-item': checkHeight }, { 'stagger-item-out': !checkHeight }]">
            <div class="skill_section_title_wrap">
                <span class="section_title">SKILLS</span>
            </div>
        </div>
        <div class="skill_container" :class="[{ 'stagger-item': checkHeight }, { 'stagger-item-out': !checkHeight }]" v-for="(skill, index) in skills" :key="index">
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
            checkHeight: false,
            durationList: [],
            skills: {
                frontEnd: [
                    { id: 0, label: "HTML5", value: "75" },
                    { id: 1, label: "CSS3", value: "70" },
                    { id: 2, label: "Javascript", value: "65" },
                    { id: 3, label: "Vue.js", value: "75" },
                    { id: 4, label: "React.js", value: "50" },
                ],
                backEnd: [
                    { id: 5, label: "Django", value: "50" },
                    { id: 6, label: "Spring", value: "20" },
                ],
                configurationManagement: [{ id: 7, label: "GitHub", value: "70" }],
                communication: [
                    { id: 8, label: "Slack", value: "80" },
                    { id: 9, label: "Figma", value: "80" },
                    { id: 10, label: "Jira", value: "70" },
                ],
            },
        };
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
            for (let i = 0; i < this.skills.frontEnd.length + this.skills.backEnd.length + this.skills.configurationManagement.length + this.skills.communication.length; i++) {
                duration += 0.5;
                this.durationList.push(duration);
            }
        },
    },

    watch: {
        scrollHeight() {
            if (this.scrollHeight >= document.getElementsByClassName("section_skill")[0].offsetTop - 400) {
                this.checkHeight = true;
            } else {
                this.checkHeight = false;
            }
        },
    },
};
</script>
<style scoped>
@import url("./skill.css");
</style>
