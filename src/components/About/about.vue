<template>
    <div class="section_myinfo">
        <div class="myinfo_content" :class="[{ 'stagger-item': checkHeight }, { 'stagger-item-out': !checkHeight && !firstLoad }, { info_opacity_zero: firstLoad }]">
            <div class="myinfo_section_title_wrap">
                <span class="section_title">ABOUT ME</span>
            </div>
        </div>
        <div class="myinfo_profile-infos" :class="[{ 'stagger-item': checkHeight }, { 'stagger-item-out': !checkHeight && !firstLoad }, { info_opacity_zero: firstLoad }]">
            <div class="myinfo_profile-info-wrapper" v-for="my_item in myData" :key="my_item.label">
                <div class="myinfo_profile-info">
                    <div class="myinfo_profile-img-wrapper"><img class="myinfo_profile-img" :src="my_item.url" /></div>
                    <div class="AboutMe_field">
                        <div class="AboutMe_field-label">{{ my_item.label }}</div>
                        <div class="AboutMe_field-value">{{ my_item.value }}</div>
                    </div>
                </div>
            </div>
        </div>
        <div class="myinfo_container">
            <div class="myinfo_introduce" :class="[{ 'stagger-item': checkHeight }, { 'stagger-item-out': !checkHeight && !firstLoad }, { info_opacity_zero: firstLoad }]">
                <div class="myinfo_introduce_title">성장하는 개발자</div>
                <div class="myinfo_introduce_text">
                    안녕하세요! 프론트 엔드 개발자 하현준입니다. <br />대학교 2학년 때 나만의 웹사이트를 만들면서 나 자신이 원하는걸 할 수 있다는 것에 흥미를 느꼈습니다. <br />그 후 인턴 생활을 하면서 Front-End Framework 인 Vue.js를 사용해
                    업무를 하게 되었고, 직접 서비스를 구현해보고, 유지/보수하면서 프론트엔드 개발자로 진로에 대한 확실한 방향을 잡았습니다.<br />
                    이를 토대로 동시에 인턴 생활을 하면서 학교의 가장 큰 프로젝트를 Vue를 사용하여 학생증 웹앱을 만들면서 프론트 엔드 업무를 맡아 마무리하였습니다.<br /><br />
                    현재는 Vue뿐만 아니라 React를 같이 공부하고 있으며, React를 사용한 프로젝트를 진행중입니다.
                    <br />
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: "About",
    props: {
        scrollHeight: Number,
    },
    data() {
        return {
            firstLoad: false,
            checkHeight: false,
            myData: [
                { label: "이름", value: "하현준", url: require("@/assets/images/aboutme/user.png") },
                { label: "이메일", value: "haryan96@naver.com", url: require("@/assets/images/aboutme/email.png") },
                { label: "연락처", value: "T. +82 (0)10-7167-3708", url: require("@/assets/images/aboutme/call.png") },
            ],
        };
    },
    mounted() {
        if (this.scrollHeight < document.getElementsByClassName("section_myinfo")[0].offsetTop - 200) {
            this.firstLoad = true;
        }
    },

    watch: {
        scrollHeight() {
            if (this.scrollHeight >= document.getElementsByClassName("section_myinfo")[0].offsetTop - 200) {
                if (this.firstLoad) this.firstLoad = false;
                this.checkHeight = true;
            } else {
                this.checkHeight = false;
            }
        },
    },
    methods: {},
};
</script>

<style scoped>
@import url("./about.css");
</style>
