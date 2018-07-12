<template>
    <div class="main">
        <p>福居网> 百科</p>

        <div class="SH-title-bottom">
            <div>
                <input type="text" placeholder="搜索">
                <button>搜索</button>
            </div>
        </div>

    </div>
</template>

<script>
    export default {
        name: "seach"
    }
</script>

<style scoped lang="less">
    .main{
        width: 1100px;
        margin: 0 auto;
    p{
        height: 70px;
        line-height: 60px;
        color: #7f828b;
        font-size: 14px;
    }
    .SH-title-bottom{
        height: 70px;
        width: 1100px;
        margin: 0 auto;
        line-height: 70px;
        color: #7f828b;
        font-size: 14px;
    input{
        outline:none;
        font-size: 15px;
        padding: 0 0 0 20px;
        background: #eee;
        border: none;
        height: 60px;
        width: 720px;
    }
    button{
        height: 60px;
        width: 160px;
        background: #c30d23;
        border: none;
        font-size: 16px;
        color: white;
    }
    }
    }
</style>