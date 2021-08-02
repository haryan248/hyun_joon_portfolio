<template>
    <div>
        <Banner />
        <!-- 내소개 -->
        <About />
        <!-- 스킬 -->
        <div></div>
        <!-- 프로젝트 -->
        <Projects />

        <!-- 커리어 -->
        <Career />
    </div>
</template>

<script>
import Banner from "../../components/Banner/banner.vue";
import About from "../../components/About/about.vue";
import Projects from "../../components/Project/project.vue";
import Career from "../../components/Career/career.vue";

export default {
    name: "Maincontent",
    components: { Projects, About, Career, Banner },
    data() {
        return {
            projects: [
                {
                    participant: { label: "참여 인원", value: "5 명" },
                    duration: { label: "개발 기간", value: "21.04 ~ 21.07" },
                    function: { label: "주요 기능", value: "회원가입, 회원찾기, 간편비밀번호 백업,출입 여부 확인, QR 체크인, 다크모드, 프로필 변경" },
                    frontend: { label: "Front-End", value: "Vue.js" },
                    backend: { label: "Back-End", value: "Django REST Framework" },
                },
            ],
        };
    },
};
</script>
<style scoped>
@import "./main-content.css";
</style>
