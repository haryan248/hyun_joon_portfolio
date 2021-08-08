<template>
    <div class="section_myinfo">
        <div class="myinfo_content" :class="computedClass">
            <div class="myinfo_section_title_wrap">
                <span class="section_title border_bottom">ABOUT ME</span>
            </div>
        </div>
        <!-- profile -->
        <div class="myinfo_profile-infos" :class="computedClass">
            <div class="myinfo_profile-info-wrapper" v-for="my_item in myData" :key="my_item.label">
                <div class="myinfo_profile-info">
                    <div class="myinfo_profile-img-wrapper"><img class="myinfo_profile-img" :src="my_item.url" /></div>
                    <div class="aboutMe_field">
                        <div class="aboutMe_field-label">{{ my_item.label }}</div>
                        <div class="aboutMe_field-value">{{ my_item.value }}</div>
                    </div>
                </div>
            </div>
        </div>
        <!-- information -->
        <div class="myinfo_container">
            <div class="myinfo_introduce" :class="computedClass">
                <div class="myinfo_img-wrapper">
                    <img class="myinfo_img" :src="profileImg" />
                </div>
                <div class="myinfo_introduce-wrapper">
                    <div class="myinfo_introduce_title">성장하는 개발자</div>
                    <div class="myinfo_introduce_text">
                        안녕하세요! 배우는걸 항상 재밌어하고 성장하는 프론트 엔드 개발자 하현준입니다. <br />대학교 2학년 때 나만의 웹사이트를 만들면서 나 자신이 원하는걸 할 수 있다는 것에 흥미를 느꼈습니다. <br /><br />그 후 인턴 생활을
                        하면서 Front-End Framework 인 Vue.js를 사용해 업무를 하게 되었고, 직접 서비스를 구현해보고, 유지/보수하면서 프론트엔드 개발자로 진로에 대한 확실한 방향을 잡았습니다. 이를 토대로 동시에 인턴 생활을 하면서 학교의 가장
                        큰 프로젝트를 Vue를 사용하여 학생증 웹앱을 만들면서 프론트 엔드 업무를 맡아 마무리하였습니다.<br /><br />
                        현재는 Vue뿐만 아니라 React를 같이 공부하고 있으며, React를 사용한 프로젝트를 진행중입니다.
                        <br />
                    </div>
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
            aboutElement: document.getElementsByClassName("section_myinfo"),
            profileImg: require("@/assets/images/aboutme/HJ.jpg"),
            myData: [
                { label: "이름", value: "하현준", url: require("@/assets/images/aboutme/user.png") },
                { label: "이메일", value: "haryan96@gmail.com", url: require("@/assets/images/aboutme/email.png") },
                { label: "연락처", value: "T. +82 (0)10-7167-3708", url: require("@/assets/images/aboutme/call.png") },
            ],
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
            if (this.scrollHeight >= this.aboutElement[0]?.offsetTop - 400) {
                return true;
            }
            return false;
        },
    },
};
</script>

<style scoped>
@import url("./about.css");
</style>
