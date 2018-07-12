<template>
    <div class="SH-content-big">
        <div class="SH-content-title">
            <img src="../assets/img/logo.png">
            <a href="">百科</a>
            <a href="">专题</a>
        </div>
    </div>
</template>

<script>
    export default {
        name: "encyand"
    }
</script>

<style scoped lang="less">
    .SH-content-big{
        width: 100%;
        border-bottom: 1px solid #ccc;
        .SH-content-title{
            height: 80px;
            line-height: 80px;
            width: 1100px;
            margin: 0 auto;
            background: white;
            img{
                vertical-align: middle;
                margin-top: 0px;
                margin-right: 135px;
            }
            a{
                font-size: 16px;
                color: black;
                margin: 0 0 0 50px;
            }
            a:hover{
                color: red;
            }
        }
    }
</style>