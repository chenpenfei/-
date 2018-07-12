<template>
    <div class="SH-content-big">
        <div class="SH-content-title">
                <span class="item1">
                    <a href="/">
                        <img src="../assets/img/logo.png">
                    </a>
                    <span class="item1-r" @click="click">呼和浩特
                        <img src="../assets/img/xia.png"></span>
                </span>
            <a href="" type="choice">在售</a>
            <a href="" type="choice">小区</a>
            <a href="" type="choice">地图找房</a>
            <a href="" type="choice">计算器</a>
            <a href="" type="choice">去估价</a>
        </div>

        <div class="selected" v-if="show">
            <div id="back">
                <i class="el-icon-close" @click="back"></i>
            </div>
            <div id="content">
                <h2>选择区县</h2>
                <p v-model="area">呼和浩特</p>
                <ul>
                    <li :value="area1">H 回民区</li>
                    <li>J 金桥开发区</li>
                    <li>R 如意开发区</li>
                    <li>S 赛罕区</li>
                    <li>X 新城区</li>
                    <li>Y 玉泉区</li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "encyandtwo",
        data() {
            return {
                show: "",
            }
        },
        methods: {
            click() {
                this.show = true
            },
            back() {
                this.show = false
            },
        }
    }
</script>

<style scoped lang="less">
    .SH-content-big {
        width: 100%;
        border-bottom: 1px solid #ccc;
        .SH-content-title {
            height: 80px;
            line-height: 80px;
            width: 1100px;
            margin: 0 auto;
            background: white;
            .item1 {
                a {

                    overflow: auto;
                    img {
                        vertical-align: middle;
                    }
                }
                span {
                    padding: 6px;
                    margin: 0 0 0 16px;
                    border: 1px solid #777;
                    border-radius: 25px;
                    img {
                        margin: 0 0 5px 0;
                        vertical-align: middle;
                    }
                }
            }
            a[type] {
                font-size: 16px;
                color: black;
                margin: 0 10px 0 30px;
            }
            a[type]:hover {
                color: red;
            }
        }
        .selected {
            background: white;
            position: fixed;
            top: 170px;
            right: 300px;
            z-index: 999;
            height: 350px;
            width: 700px;
            #content {
                margin: 0 40px;
            }
            #back {
                margin: 8px 8px 0 0;
                color: #7f828b;
                font-size: 28px;
                text-align: right;
            }
            h2 {
                font-size: 22px;
                color: #333;
                padding: 0 0 8px 0;
                border-bottom: 1px solid #7f828b;
            }
            p {
                font-size: 18px;
                margin: 20px 0;
            }
            li {
                list-style-type: none;
                margin: 5px 0;
            }
        }
    }
</style>