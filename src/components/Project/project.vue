<template>
    <div>
        <section class="section_project">
            <div class="project_content">
                <div class="project_section_title_wrap">
                    <span class="section_title">PROJECTS</span>
                </div>
                <div class="project_container">
                    <div class="project_img"></div>
                    <div class="project_intro">
                        <div class="project_intro_title"><span class="highlight">01</span> BlockChain 학생증</div>
                        <div class="project_intro_text">
                            <div class="project_intro-description">
                                <p>
                                    블록체인 및 DID 기반 학생증 발급 시스템입니다. 현재 지원하는 서비스는 학생증 발급, 강의동 출입기록, 출입 여부 확인, QR 코드 발급 및 인증이 있습니다.
                                    <br /><br />
                                    UPass를 학생들은 자신의 데이터를 중앙 집중된 형태의 데이터베이스에 저장하지 않고 분산 환경인 블록체인에 기록하고 인증합니다. 인증된 학생 정보를 활용하여 학생증을 발급하고, 발급받은 학생증을 활용하여
                                    서비스를 이용하게 됩니다. 서비스 영역의 예시로는 강의동(건물) 출입기록, 학식 주문, 장소 대여 등이 존재합니다.
                                </p>
                            </div>
                            <div class="project_description" v-for="(project_item, index) in projects[0]" :key="index">
                                <div class="projects_label">{{ project_item.label }}</div>
                                <div class="projects_value">{{ project_item.value }}</div>
                            </div>
                            <div class="project_intro_button_box">
                                <div class="project_intro_button" onclick="youtube_on('om3f3AuP0Tc')">
                                    YouTube 보기
                                </div>
                                <div class="project_intro_button" onclick="github_on('React-sns')">
                                    Github 보기
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="project_container">
                    <div class="project_intro">
                        <div class="project_intro_title"><span class="highlight">02</span> 포르쉐 웹 쇼핑몰</div>
                        <div class="project_intro_text">
                            <div class="project_intro-description">
                                <p>
                                    JSP 언어를 사용한 포르쉐 웹 쇼핑몰 제작
                                    <br /><br />
                                    웹 프로그래밍 교과목에서 HTML, CSS, JavaScript 만으로 진행되었던 프로젝트에서 부족함을 느꼈고, 지능웹설계 교과목에서 정적인 웹페이지를 동적인 웹페이지로 해당 프로젝트를 발전, 확장 및 향상시켰습니다.
                                </p>
                            </div>
                            <div class="project_description" v-for="(project_item, index) in projects[1]" :key="index">
                                <div class="projects_label">{{ project_item.label }}</div>
                                <div class="projects_value">{{ project_item.value }}</div>
                            </div>
                            <div class="project_intro_button_box">
                                <div class="project_intro_button" onclick="youtube_on('om3f3AuP0Tc')">
                                    YouTube 보기
                                </div>
                                <div class="project_intro_button" onclick="github_on('React-sns')">
                                    Github 보기
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="project_img project_img1" style="animation: 0.7s ease-out 0s 1 normal both running slide-right; opacity: 1;"></div>
                </div>
            </div>
        </section>
    </div>
</template>
<script>
export default {
    name: "Project",
    data() {
        return {
            projects: [
                {
                    participant: { label: "참여 인원", value: "5 명" },
                    duration: { label: "개발 기간", value: "21.04 ~ 21.07" },
                    function: { label: "주요 기능", value: "회원가입, 회원찾기, 간편비밀번호 백업,출입 여부 확인, QR 체크인, 다크모드, 프로필 변경" },
                    frontend: { label: "Front-End", value: "Vue.js" },
                    backend: { label: "Back-End", value: "Django REST Framework" },
                    deployment: { label: "Deployment", value: "Nginx, Naver Cloud Platform" },
                },
                {
                    participant: { label: "참여 인원", value: "1 명" },
                    duration: { label: "개발 기간", value: "2020.09 ~ 2021.12" },
                    function: { label: "주요 기능", value: "로그인, 회원가입, 회원정보 수정, 차량 등록, 차량 삭제, 게시판 등록, 게시판 삭제 등" },
                    frontend: { label: "Front-End", value: "JSP" },
                    backend: { label: "Back-End", value: "JSP, MySQL" },
                    deployment: { label: "Deployment", value: "AWS(EC2)" },
                },
            ],
        };
    },
};
</script>
<style scoped>
@import url("./project.css");
</style>
