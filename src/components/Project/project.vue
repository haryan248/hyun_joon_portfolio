<template>
    <section class="section_project">
        <div class="project_content">
            <div class="project_section_title_wrap" :class="[{ 'stagger-item': checkHeight }, { 'stagger-item-out': !checkHeight }]">
                <span class="section_title">PROJECTS</span>
            </div>
            <ProjectList v-for="(projects, index) in projects" :key="index" :index="index" :projects="projects" :scrollHeight="scrollHeight" />
        </div>
    </section>
</template>
<script>
import ProjectList from "./components/projectList/projectList.vue";

export default {
    name: "Project",
    props: {
        scrollHeight: Number,
    },
    components: {
        ProjectList,
    },
    data() {
        return {
            projects: [
                {
                    title: "블록체인 학생증",
                    description:
                        "<p>JSP 언어를 사용한 포르쉐 웹 쇼핑몰 제작<br /><br />웹 프로그래밍 교과목에서 HTML, CSS, JavaScript 만으로 진행되었던 프로젝트에서 부족함을 느꼈고, 지능웹설계 교과목에서 정적인 웹페이지를 동적인 웹페이지로 해당 프로젝트를 발전, 확장 및 향상시켰습니다.</p>",
                    participant: { label: "참여 인원", value: "5 명" },
                    duration: { label: "개발 기간", value: "2021.04 ~ 2021.07" },
                    function: { label: "주요 기능", value: "회원가입, 회원찾기, 간편비밀번호 백업,출입 여부 확인, QR 체크인, 다크모드, 프로필 변경" },
                    frontend: { label: "Front-End", value: "Vue.js" },
                    backend: { label: "Back-End", value: "Django REST Framework" },
                    deployment: { label: "Deployment", value: "Nginx, Naver Cloud Platform" },
                    youtube: "https://www.youtube.com/watch?v=_3wVc06CsuM&list=PLJ8elSeS2xGwbtYUIyoqQqnlH04DBzqB6&index=17",
                    github: "https://github.com/haryan248/BlockChain_Capstone_FrontEnd_Vue",
                },
                {
                    title: "포르쉐 웹 쇼핑몰",
                    description:
                        " <p>블록체인 및 DID 기반 학생증 발급 시스템입니다. 현재 지원하는 서비스는 학생증 발급, 강의동 출입기록, 출입 여부 확인, QR 코드 발급 및 인증이 있습니다.<br /><br />UPass를 학생들은 자신의 데이터를 중앙 집중된 형태의 데이터베이스에 저장하지 않고 분산 환경인 블록체인에 기록하고 인증합니다. 인증된 학생 정보를 활용하여 학생증을 발급하고, 발급받은 학생증을 활용하여 서비스를 이용하게 됩니다. 서비스 영역의 예시로는 강의동(건물) 출입기록, 학식 주문, 장소 대여 등이 존재합니다.</p>",
                    participant: { label: "참여 인원", value: "1 명" },
                    duration: { label: "개발 기간", value: "2020.09 ~ 2021.12" },
                    function: { label: "주요 기능", value: "로그인, 회원가입, 회원정보 수정, 차량 등록, 차량 삭제, 게시판 등록, 게시판 삭제 등" },
                    frontend: { label: "Front-End", value: "JSP" },
                    backend: { label: "Back-End", value: "JSP, MySQL" },
                    deployment: { label: "Deployment", value: "AWS(EC2)" },
                    youtube: "https://youtu.be/8i_04GkhwWI",
                    github: "https://github.com/haryan248/Intelligent_Web_Design/wiki",
                },
                {
                    title: "포트폴리오 사이트",
                    description: " <p>Vue.js 기반으로 제작한 포트폴리오 사이트입니다.<br /><br />저의 소개, 프로젝트, 인턴 경험을 보기 쉽게 나열한 포트폴리오 사이트입니다.</p>",
                    participant: { label: "참여 인원", value: "1 명" },
                    duration: { label: "개발 기간", value: "2021.07.31 ~ 2021.08.10" },
                    function: { label: "주요 내용", value: "About me, Skills, Projects, Career" },
                    frontend: { label: "Front-End", value: "Vue.js" },
                    deployment: { label: "Deployment", value: "github" },
                    github: "https://github.com/haryan248/hyun_joon_portfolio",
                },
            ],
            checkHeight: false,
        };
    },
    mounted() {},
    watch: {
        scrollHeight() {
            if (this.scrollHeight >= document.getElementsByClassName("section_project")[0].offsetTop - 400) {
                this.checkHeight = true;
            } else {
                this.checkHeight = false;
            }
        },
    },
};
</script>
<style scoped>
@import url("./project.css");
</style>
