<template>
    <div class="all">
        <my-top2/>
        <div class="header-content">
            <div class="header">

                <div class="region">
                    <a href="/">
                        <img src="../assets/img/logo.png">
                    </a>
                    <span class="item1-r" @click="click">
                        呼和浩特
                        <img src="../assets/img/xia.png">
                    </span>
                </div>

                <div class="login">
                    首页
                </div>
                <div class="houses">
                    楼盘
                </div>

                <div class="seach">
                    <input type="text">
                    <el-button id="seach-btn1">搜索</el-button>
                    <el-button id="seach-btn2">地图找房</el-button>
                </div>
            </div>

            <div class="selected" v-if="show">
                <div id="back">
                    <i class="el-icon-close" @click="back"></i>
                </div>
                <div id="content">
                    <h2>选择区县</h2>
                    <p>呼和浩特</p>
                    <ul>
                        <li >H 回民区</li>
                        <li>J 金桥开发区</li>
                        <li>R 如意开发区</li>
                        <li>S 赛罕区</li>
                        <li>X 新城区</li>
                        <li>Y 玉泉区</li>
                    </ul>
                </div>
            </div>

        </div>

        <div class="content-swipe">
            <el-carousel trigger="click" height="505px"
                         indicator-position="none" arrow="never">
                <el-carousel-item >
                    <img src="../assets/img/lbt.jpg" height="100%" width="100%">
                </el-carousel-item>
                <el-carousel-item >
                    <img src="../assets/img/lbt.jpg" height="100%" width="100%">
                </el-carousel-item>
            </el-carousel>


        </div>

        <div class="main">
            <div class="swipe-left">
                <div class="selected">
                    <el-select v-model="value" placeholder="区域"
                               style="text-align: center;text-align-last: center;">
                        <el-option
                            v-for="item in options"
                            :key="item.value"
                            :label="item.label"
                            :value="item.value" class="option" style="padding: 0 0 0 70px">
                        </el-option>
                    </el-select>
                </div>
                <div class="selected">
                    <el-select v-model="value" placeholder="区域" style="text-align: center;text-align-last: center">
                        <el-option
                                v-for="item in options"
                                :key="item.value"
                                :label="item.label"
                                :value="item.value" class="option" style="padding: 0 0 0 70px">
                        </el-option>
                    </el-select>
                </div>
                <div class="selected">
                    <el-select v-model="value" placeholder="区域" style="text-align: center;text-align-last: center">
                        <el-option
                                v-for="item in options"
                                :key="item.value"
                                :label="item.label"
                                :value="item.value" class="option" style="padding: 0 0 0 70px">
                        </el-option>
                    </el-select>
                </div>
                <div class="selected">
                    <el-select v-model="value" placeholder="区域" style="text-align: center;text-align-last: center">
                        <el-option
                                v-for="item in options"
                                :key="item.value"
                                :label="item.label"
                                :value="item.value" class="option" style="padding: 0 0 0 70px">
                        </el-option>
                    </el-select>
                </div>
                <div class ="swipe-btn">
                    <a href="">筛选</a>
                </div>
            </div>

            <div class="price-content">
                <img src="../assets/img/content.png" alt="">
            </div>

        </div>

        <div class="actual">
            <a href="/"><img src="../assets/img/falsh.png" style="margin-bottom: 80px"></a>

            <div class="good-house-2">
                <div class="house2">
                    <div id="house2-0">
                        <p id="moon">荷塘月色</p>
                        <p id="site">呼和浩特市赛罕区银河南街东段（内蒙古党校西侧）</p>
                    </div>
                    <div id="img-scale">
                        <img src="../assets/img/zjbg-1.jpg">
                    </div>
                    <p id="house2-l">
                        <span id="average">均价： </span>
                        <span id="money">8500元/平</span>
                        <span id="small">小高层</span>
                    </p>
                    <p id="house2-r">3室2厅2卫 128.80㎡ </p>
                </div>
                <div class="house2-middle">
                    <div id="house2-0">
                        <p id="moon">荷塘月色</p>
                        <p id="site">呼和浩特市赛罕区银河南街东段（内蒙古党校西侧）</p>
                    </div>
                    <div id="img-scale">
                        <img src="../assets/img/zjbg-2.jpg">
                    </div>
                    <p id="house2-l">
                        <span id="average">均价： </span>
                        <span id="money">8500元/平</span>
                        <span id="small">小高层</span>
                    </p>
                    <p id="house2-r">3室2厅2卫 128.80㎡ </p>
                </div>
                <div class="house2">
                    <div id="house2-0">
                        <p id="moon">荷塘月色</p>
                        <p id="site">呼和浩特市赛罕区银河南街东段（内蒙古党校西侧）</p>
                    </div>
                    <div id="img-scale">
                        <img src="../assets/img/zjbg-2.jpg">
                    </div>
                    <p id="house2-l">
                        <span id="average">均价： </span>
                        <span id="money">8500元/平</span>
                        <span id="small">小高层</span>
                    </p>
                    <p id="house2-r">3室2厅2卫 128.80㎡ </p>
                </div>
            </div>
            <div class="good-house-2">
                <div class="house2">
                    <div id="house2-0">
                        <p id="moon">荷塘月色</p>
                        <p id="site">呼和浩特市赛罕区银河南街东段（内蒙古党校西侧）</p>
                    </div>
                    <div id="img-scale">
                        <img src="../assets/img/zjbg-1.jpg">
                    </div>
                    <p id="house2-l">
                        <span id="average">均价： </span>
                        <span id="money">8500元/平</span>
                        <span id="small">小高层</span>
                    </p>
                    <p id="house2-r">3室2厅2卫 128.80㎡ </p>
                </div>
                <div class="house2-middle">
                    <div id="house2-0">
                        <p id="moon">荷塘月色</p>
                        <p id="site">呼和浩特市赛罕区银河南街东段（内蒙古党校西侧）</p>
                    </div>
                    <div id="img-scale">
                        <img src="../assets/img/zjbg-2.jpg">
                    </div>
                    <p id="house2-l">
                        <span id="average">均价： </span>
                        <span id="money">8500元/平</span>
                        <span id="small">小高层</span>
                    </p>
                    <p id="house2-r">3室2厅2卫 128.80㎡ </p>
                </div>
                <div class="house2">
                    <div id="house2-0">
                        <p id="moon">荷塘月色</p>
                        <p id="site">呼和浩特市赛罕区银河南街东段（内蒙古党校西侧）</p>
                    </div>
                    <div id="img-scale">
                        <img src="../assets/img/zjbg-2.jpg">
                    </div>
                    <p id="house2-l">
                        <span id="average">均价： </span>
                        <span id="money">8500元/平</span>
                        <span id="small">小高层</span>
                    </p>
                    <p id="house2-r">3室2厅2卫 128.80㎡ </p>
                </div>
            </div>
        </div>
        <my-sidebar/>
        <my-footer/>
    </div>
</template>

<script>
    import MySidebar from '../components/sidebar'
    import MyFooter from '~/components/Footer.vue'
    import MyTop2 from '../components/top2'
    export default {
        name: "newHouseIndex",
        components:{
            MyFooter,MyTop2,MySidebar
        },
        data(){
            return{
                show:"",
                options: [{
                    value: '选项1',
                    label: '不限'
                }, {
                    value: '选项2',
                    label: '金桥开发区'
                }, {
                    value: '选项3',
                    label: '如意开发区'
                }, {
                    value: '选项4',
                    label: '玉泉区'
                }, {
                    value: '选项5',
                    label: '回民区'
                }],
                value: ''
            }
        },
        methods: {
            click(){
                this.show = true
            },
            back(){
                this.show = false
            },

        }
    }
</script>

<style scoped lang="less">
    input{
        outline: none;
    }
.all {
    width: 100%;
    .header-content{
        width: 1100px;
        margin: 0 auto;
        .header{
            height: 80px;
            line-height: 80px;
            .region{
                width: 330px;
                float: left;
                margin-right: 10px;
                a {
                    position: relative;
                    top: 15px;

                }
                span {
                    cursor: pointer;
                    padding: 6px;
                    margin: 0 0 0 20px;
                    border: 1px solid #777;
                    border-radius: 25px;
                    img {
                        vertical-align: middle;
                    }
                }
            }
            .login{
                color: red;
                font-size: 16px;
                text-align: left;
                width: 80px;
                float: left;
                cursor: pointer;
            }
            .houses{
                font-size: 16px;
                text-align: left;
                width: 80px;
                float: left;
                cursor: pointer;
            }
            .seach{
                float: left;
                width: 568px;
                margin: 0 16px;
                input{
                    font-size: 16px;
                    width: 300px;
                    height: 35px;
                }
                #seach-btn1{
                    font-size: 16px;
                    width: 102px;
                    height: 40px;
                    background: #c30d23;
                    color: #fff;
                }
                #seach-btn2{
                    font-size: 16px;
                    width: 150px;
                    height: 40px;
                    background: #5f1985;
                    color: #fff;
                }
            }
        }
        .selected{
            background: white;
            position: fixed;
            top: 170px;
            right: 300px;
            z-index: 999;
            height: 350px;
            width: 700px;
        }
    }

    .main{
        height: 120px;
        width: 1100px;
        margin: 80px auto 0 auto;
        position: relative;
        .swipe-left{
            text-align: center;
            position: absolute;
            left: 22%; top: -88%;
            transform: translate(-81%, -95%);
            z-index: 999;
            height: 440px;
            width: 300px;
            background: rgba(255, 0, 0, 0.4);
            padding-top: 65px;
            .selected{
                width: 198px;
                height: 32px;

                margin: 10px auto 50px auto;
                select{
                    font-size: 16px;

                    margin: 20px 0;
                    text-align: center;
                    text-align-last: center;
                    width: 198px;
                    height: 30px;
                    border-radius: 4px;
                }
            }
            .swipe-btn{
                font-size: 16px;
                margin: 70px auto 0 auto;
                width: 200px;
                height: 50px;
                line-height: 50px;
                background: #fff;
                border-radius: 5px;
                a{

                    width: 200px;
                    height: 50px;
                }
            }
        }
        .price-content{
            height: 100px;
            background: yellow;
            img{
                width: 1100px;
                height: 100px;
            }
        }
    }

    .actual{
        width: 1100px;
        margin: 0 auto;
        .good-house-2 {
            height: 365px;

            .house2 {
                position: relative;
                float: left;
                height: 345px;
                width: 342px;
                #img-scale{
                    overflow: hidden;
                    width: 340px;
                    height: 255px;
                    img {
                        height: 255px;
                        width: 340px;
                        transition: all 0.6s;
                    }
                    img:hover{
                        transform:scale(1.1);//设置缩放比例
                    }
                }
                #house2-0 {
                    background-color: rgba(0, 0, 0, 0.5);
                    position: absolute;
                    bottom: 90px;
                    left: 0;
                    z-index: 998;
                    padding-left: 8px;
                    width: 332px;
                    height: 82px;
                    #moon{
                        color: white;
                        font-size: 20px;
                        font-weight: bold;
                        margin: 5px 0 10px 0;
                    }
                    #site{
                        color: white;
                        font-size: 16px;
                    }
                }
                #house2-l {
                    clear: both;
                    margin: 30px 0 10px 0;
                    #average{
                        font-size: 16px;
                    }
                    #money{
                        font-size: 16px;
                        color: red;
                    }
                    #small{
                        font-size: 14px;
                        padding: 3.5px 7px;
                        background: #ddd;
                        float: right;
                    }
                }
                #house2-r {
                    color: #7f828b;
                    font-size: 14px;
                    margin-top: 12px;
                }

            }

            .house2-middle {
                position: relative;
                float: left;
                height: 345px;
                width: 342px;
                margin: 0 37px;
                #img-scale{
                    overflow: hidden;
                    width: 340px;
                    height: 255px;
                    img {
                        height: 255px;
                        width: 340px;
                        transition: all 0.6s;
                    }
                    img:hover{
                        transform:scale(1.1);//设置缩放比例
                    }
                }
                #house2-0 {
                    background-color: rgba(0, 0, 0, 0.5);
                    position: absolute;
                    bottom: 90px;
                    left: 0;
                    z-index: 998;
                    padding-left: 8px;
                    width: 332px;
                    height: 82px;
                    #moon{
                        color: white;
                        font-size: 20px;
                        font-weight: bold;
                        margin: 5px 0 10px 0;
                    }
                    #site{
                        color: white;
                        font-size: 16px;
                    }
                }
                #house2-l {
                    clear: both;
                    margin: 30px 0 10px 0;
                    #average{
                        font-size: 16px;
                    }
                    #money{
                        font-size: 16px;
                        color: red;
                    }
                    #small{
                        font-size: 14px;
                        padding: 3.5px 7px;
                        background: #ddd;
                        float: right;
                    }
                }
                #house2-r {
                    color: #7f828b;
                    font-size: 14px;
                    margin-top: 12px;
                }

            }
        }
    }
}
</style>