<template>
    <div class="career_companies">
        <div class="career_company">
            <div class="career_logo-container">
                <div class="career_logo-wrapper">
                    <img class="career_logo" :src="careers.logo" />
                </div>
            </div>
            <div class="career_info">
                <div class="career_title">{{ careers.company }}</div>
                <div class="career_period">{{ careers.period }}</div>
                <div class="career_description" v-html="careers.description"></div>
                <ul class="career_works">
                    <div v-for="(work, index) in careers.works" :key="index">
                        <h4 class="career_works-title">{{ work.title }}</h4>
                        <h5 class="career_works-period">{{ work.period }}</h5>
                        <div v-for="(work_item, index) in work.description" :key="index">
                            <li class="career_works-item">{{ work_item }}</li>
                        </div>
                    </div>
                </ul>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: "careerList",
    props: {
        careers: Object,
    },
    data() {
        return {};
    },
};
</script>
<style>
@import url("./career-list.css");
</style>
