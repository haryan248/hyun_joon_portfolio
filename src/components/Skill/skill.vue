<template>
    <div>
        <section class="section_skill">
            <div class="skill_content" :class="[{ 'stagger-item': checkHeight }, { 'stagger-item-out': !checkHeight }]">
                <div class="skill_section_title_wrap">
                    <span class="section_title">SKILLS</span>
                </div>
            </div>
            <div class="skill_container">
                <div class="status_content">
                    <div class="status_bar-title">HTML5</div>
                    <div class="status_bar-item">
                        <div class="status_bar-percent">75%</div>
                    </div>
                </div>
                <div class="status_content">
                    <div class="status_bar-title">HTML5</div>

                    <div class="status_bar-item">
                        <div class="status_bar-percent">60%</div>
                    </div>
                </div>
                <div class="status_content">
                    <div class="status_bar-title">HTML5</div>
                    <div class="status_bar-item">
                        <div class="status_bar-percent">75%</div>
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
        return { checkHeight: false };
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
