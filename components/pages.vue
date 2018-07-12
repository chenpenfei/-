<template>
    <div class="page">
        <span>首页</span>
        <span>上一页</span>
        <span>1</span>
        <span>2</span>
        <span>3</span>
        <span>...</span>
        <span>135</span>
        <span>上一页</span>
        <span>末页</span>
    </div>
</template>

<script>
    export default {
        name: "pages"
    }
</script>

<style scoped lang="less">
    .page{
        clear: both;
        width: 1100px;
        text-align: right;
        height: 105px;
        line-height: 105px;
        margin: 50px auto 40px auto ;
    span{
        color: #888;
        border: 1px solid #ccc;
        border-radius: 3px;
        margin: 0 3px;
        padding:10px 15px;
        cursor: pointer;
    }
    }
</style>