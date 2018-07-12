<template>
    <header>
        <div class="item">
            <span class="item1">
                <a href="/" class="index">首页</a>
                <a href="/secondSchoolHomesList">二手房</a>
                <a href="/newHouseIndex">新房</a>
                <a href="/rentalList">租房</a>
                <a href="/schoolDistrictHousesList">学区房</a>
                <a href="/residentialQuartersList">小区</a>
                <a href="/brokerList">经纪人</a>
                <a href="/encyclopedias">百科</a>
                <a href="">
                    <el-dropdown class="line">
                      <span>在线委托</span>
                      <el-dropdown-menu slot="dropdown">
                        <el-dropdown-item>我是业主</el-dropdown-item>
                        <el-dropdown-item>帮我找房</el-dropdown-item>
                      </el-dropdown-menu>
                      </el-dropdown>
                </a>
                <a href="/tool">工具</a>
                <a href="/special">专题</a>
            </span>
            <span class="item2">
                <a href="">请登录</a>
                <span>|</span>
                <a href="/regist">立即注册</a>
            </span>
        </div>

    </header>
</template>

<script>
    export default {
        components:{

        },
        data(){
            return{
            }
        },
        created(){

        },
        methods: {
            click(){
            },
            back(){
            },

        }
    }
</script>

<style scoped lang="less">
    a {
        color: black;
        text-decoration: none;
    }
    .line{
        color: black;
        font-size: 16px;
    }

    header {
        width: 100%;
        background: #eee;
        .item {
            width: 1100px;
            margin:  0 auto;
            color: black;
            line-height: 60px;
            height: 60px;
            padding: 0 20px;
            .item1{
                font-size: 16px;
                width: 900px;
                a{
                    margin: 0 35px 0 0;

                }
           }
            .item2{
                float: right;
                font-size: 12px;
               text-align: right;
                span{
                    margin: 0 10px;
                }
            }
        }

    }
</style>











