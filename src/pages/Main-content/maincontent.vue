<template>
    <div>
        <!-- banner -->
        <Banner :scrollHeight="scrollHeight" :checkWidth="checkWidth" />
        <!-- about me -->
        <About :scrollHeight="scrollHeight" />
        <!-- skill -->
        <Skill :scrollHeight="scrollHeight" />
        <!-- projects -->
        <Projects :scrollHeight="scrollHeight" />
        <!-- career -->
        <Career />
    </div>
</template>

<script>
import Banner from "../../components/Banner/banner.vue";
import About from "../../components/About/about.vue";
import Skill from "../../components/Skill/skill.vue";
import Projects from "../../components/Project/project.vue";
import Career from "../../components/Career/career.vue";

export default {
    name: "Maincontent",
    components: { Projects, About, Career, Banner, Skill },
    props: { scrollHeight: Number, checkWidth: Boolean },
    data() {
        return {};
    },
};
</script>
