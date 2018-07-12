<template>
    <div>
        <header class="dtop">
            <a href="" class="dtop-left"><img src="../assets/img/logo.png"></a>
            <a href="" class="dtop-right">
                <span>返回福居网首页</span>
                <img src="../assets/img/return.png">
            </a>
        </header>

        <nuxt/>

        <footer>
            <p>北京福居网网络科技有限公司|
                Copyright © 2013-2017 FOOJU Corporation,
                All Rights Reserved 福居网 版权所有| 京ICP备13012924号-1</p>
        </footer>

    </div>
</template>

<script>
    export default {
        components: {

        }
    }
</script>

<style scoped lang="less">
 a{
     text-decoration: none;
    }
.dtop{
    background: white;
    height: 80px;
    text-align: left;
    .dtop-left{
        img{
            margin: 20px 0 0px 120px;
        }
    }
    .dtop-right{
        color: #555;
        height: 40px;
        position: relative;
        top: -15px;
        left: 840px;
        span{
            font-size: 13px;
            margin: 5px;
        }
        img{
            vertical-align: middle;
        }
    }
}
footer{
    height: 70px;
    background: #dbe1ec;
   line-height: 40px;
    font-size: 14px;
    color: #777;
    text-align: center;
    position: absolute;
    bottom: -90px;
    right: 0;
    left: 0;
}
</style>