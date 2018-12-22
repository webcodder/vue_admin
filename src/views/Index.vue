<template>
    <!--<section class="container f-oh">-->
        <!--<HeadNav></HeadNav>-->

        <!--<div class="main">-->
            <!--<LeftMenu></LeftMenu>-->

            <!--<div class="right_container">-->
                <!--<transition name="fade"  mode="out-in">-->
                    <!--<router-view></router-view>-->
                <!--</transition>-->
            <!--</div>-->
        <!--</div>-->
    <!--</section>-->
    <el-container class="container">
        <el-header class="header f-oh">
            <HeadNav></HeadNav>
        </el-header>
        <el-container>
            <el-aside class="aside">
                <LeftMenu></LeftMenu>
            </el-aside>
            <el-main class="main">
                <router-view></router-view>
            </el-main>
        </el-container>
    </el-container>
</template>

<script>
    import HeadNav from '../components/HeadNav'
    import LeftMenu from "../components/LeftMenu";

    export default {
        name: "index",

        components: {
            HeadNav,
            LeftMenu
        }
    }
</script>

<style scoped>
    .container {
        width: 100%;
        height: auto;
    }

    .header{
        padding: 0;
    }

    .aside {

    }

    .main {
        background-color: #E9EEF3;
    }
</style>