<template>
    <div>
        <section class="section_skill">
            <div class="skill_content" :class="[{ 'stagger-item': checkHeight }, { 'stagger-item-out': !checkHeight }]">
                <div class="skill_section_title_wrap">
                    <span class="section_title">SKILLS</span>
                </div>
            </div>
            <!-- front-end -->
            <div class="skill_container">
                <div class="status_content" v-for="skill in skills.frontEnd" :key="skill.label">
                    <div class="status_bar-title">{{ skill.label }}</div>
                    <div class="status_bar-item">
                        <div class="status_bar-percent" :class="'percent_animation-' + skill.value">{{ skill.value }}%</div>
                    </div>
                </div>
                <!-- back-end -->
                <div class="status_content" v-for="skill in skills.backEnd" :key="skill.label">
                    <div class="status_bar-title">{{ skill.label }}</div>
                    <div class="status_bar-item">
                        <div class="status_bar-percent" :class="'percent_animation-' + skill.value">{{ skill.value }}%</div>
                    </div>
                </div>
                <!-- configuration management -->
                <div class="status_content" v-for="skill in skills.configurationManagement" :key="skill.label">
                    <div class="status_bar-title">{{ skill.label }}</div>
                    <div class="status_bar-item">
                        <div class="status_bar-percent" :class="'percent_animation-' + skill.value">{{ skill.value }}%</div>
                    </div>
                </div>
                <!-- communication -->
                <div class="status_content" v-for="skill in skills.communication" :key="skill.label">
                    <div class="status_bar-title">{{ skill.label }}</div>
                    <div class="status_bar-item">
                        <div class="status_bar-percent" :class="'percent_animation-' + skill.value">{{ skill.value }}%</div>
                    </div>
                </div>
            </div>
        </section>
    </div>
</template>
<script>
export default {
    name: "Skill",
    props: { scrollHeight: Number },
    data() {
        return {
            checkHeight: false,
            skills: {
                frontEnd: [
                    { label: "HTML5", value: "75" },
                    { label: "CSS3", value: "70" },
                    { label: "Javascript", value: "65" },
                    { label: "Vue.js", value: "75" },
                    { label: "React.js", value: "50" },
                ],
                backEnd: [
                    { label: "Django", value: "50" },
                    { label: "Spring", value: "20" },
                ],
                configurationManagement: [{ label: "GitHub", value: "70" }],
                communication: [
                    { label: "Slack", value: "80" },
                    { label: "Figma", value: "80" },
                    { label: "Jira", value: "70" },
                ],
            },
        };
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
