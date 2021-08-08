<template>
    <div class="section_career">
        <div class="career_content">
            <div class="career_section_title_wrap">
                <span class="section_title border_bottom">CAREER</span>
            </div>
        </div>
        <CareerList v-for="(careers, index) in careers" :key="index" :careers="careers" />
    </div>
</template>
<script>
import CareerList from "./components/careerList/careerList.vue";
export default {
    name: "Career",
    components: { CareerList },
    data() {
        return {
            careers: [
                {
                    company: "(주) 마켓디자이너스",
                    period: "2021.01.04 - 2021.05.18",
                    description:
                        "획일화된 학원 수업, 정해진 시간에만 진행하는 과외, 실력이 늘지 않는 일방향 온라인 강의 튜터링은 혁신적인 ‘온디맨드 러닝' 특허 기술로 시간/공간 제약 없이 전 세계 전문 튜터와 이용자를 실시간 매칭하는 온디맨드 교육 플랫폼입니다. <br /><br />튜터링(Tutoring) 앱의 신규 서비스에 프론트엔드 업무를 맡았습니다. 신규 서비스 런칭을 위해 초기 코드 작성부터 참여하였고, 사용자가 쓰며 느꼈던 불편함을 피드백 받아 고치는 작업까지 경험했습니다. 또한, 실무에서 백앤드와 API 명세서를 통해 소통하고, QA팀 선임 개발자들과 WBS로 오류를 수정하고, 디자인팀과 Figma를 통해 디자인을 수정해보며 경험을 쌓았습니다.",
                    logo: require("@/assets/images/career/tutoring/tutoring_logo.png"),
                    works: [
                        {
                            title: "▎ 튜터링 앱 신규 서비스(튜터링 플레이) 준비",
                            period: "2021.01.04 ~ 2021.02.18",
                            description: [
                                "Vue.Js를 사용해 튜터링 앱에 출시되는 신규 서비스를 런칭",
                                "초기 레이아웃 구성 및 RestAPI를 이용한 통신",
                                "Vimeo 라이브러리 적용 및 PIP 기능 대응",
                                "Vue.Js 중첩 라우팅 작업",
                                "국가 근로 인턴 기간 종료",
                            ],
                        },
                        {
                            title: "▎ 서비스 런칭 후 유지 보수",
                            period: "2021.02.19 ~ 2021.05.18",
                            description: ["계약직 조정 후 기간 연장", "사용자들의 편의성을 위한 UI/UX 개선", "코드 리팩토링 및 최적화", "컴포넌트 통일성 확보", "튜터링 플레이(튜플) QA 대응 및 admin 페이지 작업 병행"],
                        },
                    ],
                },
                {
                    company: "슈어소프트테크",
                    period: "2020.07.01 ~ 2020.08.28",
                    description:
                        "자동차,원자력,국방,철도,금융 분야에서 소프트웨어 설계부터 검수까지 검증서비스 제공하는 회사입니다. <br /><br />Linux환경에서 C++언어를 활용한 차량의 AVN(Audio, Vedio, Navigation) 모듈의 기존 Test Case들의 Frame Work를 GTest로 변경하는 것을 목표로 진행하였습니다.",
                    logo: require("@/assets/images/career/suresoft/suresoft_logo.png"),
                    works: [
                        {
                            title: "▎ 테스트 케이스 변경",
                            period: "2020.07.01 ~ 2020.08.28",
                            description: [
                                "AVN 모듈의 기존에 만들어진 차량의 TC(Test Case) 800개 가량의 API를 GTest로 변경하는 작업",
                                "Tool Chain이 변경되면서 그에 따른 업데이트를 통해 TC의 오류 해결",
                                "Vimeo 라이브러리 적용 및 PIP 기능 대응",
                                "신규 테스트 케이스 작성 및 기존 테스트 케이스 유지 보수",
                                "국가 근로 인턴 기간 종료",
                            ],
                        },
                    ],
                },
            ],
        };
    },
};
</script>
<style scoped>
@import "./career.css";
</style>
