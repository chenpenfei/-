<template>
    <div>
        <my-top/>
        <div class="SH-content">

            <div class="main">
                <p>福居网> 经纪人</p>

                <div class="SH-title-bottom">

                    <div>
                        <input type="text" placeholder="搜索">
                        <button id="map-btn1">搜索</button>
                        <button id="map-btn2">
                            <i class="iconfont icon-mendian" style="font-size: 20px"></i>
                            地图找房
                        </button>
                    </div>
                </div>

                <div class="top">
                    <div class="region">
                        <div class="region-tt">区域</div>
                        <div class="region-ct">
                            <el-checkbox @change="CheckAllRegions"
                                         v-model="checkRegions"
                                         style="float: left;margin: 0 30px 0 0;">不限</el-checkbox>
                            <el-checkbox-group v-model="checkedRegions"
                                               @change="handleCheckedRegionsChange">
                                <el-checkbox v-for="region in Regions" :label="region"
                                             :key="region" style="float: left;margin: 0 30px  0 0;">{{region}}</el-checkbox>
                            </el-checkbox-group>
                        </div>
                    </div>
                    <div class="house">
                        <div class="house-tt">筛选</div>
                        <div class="house-ct">
                            <el-checkbox-group v-model="checkedHouses">
                                <el-checkbox v-for="house in houses" :label="house"
                                             :key="house"
                                             style="float: left;margin: 0 30px  0 0;">{{house}}</el-checkbox>
                            </el-checkbox-group>
                        </div>
                    </div>
                </div>

            </div>

            <div class="resource">

                <div class="find">
                    共找到
                    <span>213 </span>
                    <span style="color: #000">名经纪人</span>
                </div>

                <div class="specific">
                    <img src="../assets/img/家居图.png">
                    <div class="photo">
                        <div id="address">武学一</div>
                        <div id="address">所属门店： 人民路店</div>
                    </div>

                    <div class="rank">
                        <div id="rank-test1">综合评分 5.0</div>
                        <div id="rank-test2">评论 0条</div>
                    </div>
                    <div class="phone">
                        <div id="phone-meter1">400-898-1018 转 3011</div>
                        <div id="phone-meter2">联系方式</div>
                    </div>
                </div>
                <div class="specific">
                    <img src="../assets/img/家居图.png">
                    <div class="photo">
                        <div id="address">武学一</div>
                        <div id="address">所属门店： 人民路店</div>
                    </div>

                    <div class="rank">
                        <div id="rank-test1">综合评分 5.0</div>
                        <div id="rank-test2">评论 0条</div>
                    </div>
                    <div class="phone">
                        <div id="phone-meter1">400-898-1018 转 3011</div>
                        <div id="phone-meter2">联系方式</div>
                    </div>
                </div>
                <div class="specific">
                    <img src="../assets/img/家居图.png">
                    <div class="photo">
                        <div id="address">武学一</div>
                        <div id="address">所属门店： 人民路店</div>
                    </div>

                    <div class="rank">
                        <div id="rank-test1">综合评分 5.0</div>
                        <div id="rank-test2">评论 0条</div>
                    </div>
                    <div class="phone">
                        <div id="phone-meter1">400-898-1018 转 3011</div>
                        <div id="phone-meter2">联系方式</div>
                    </div>
                </div>


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
            </div>

        </div>
        <my-footer/>
    </div>
</template>
<script>
    import MyFooter from '~/components/Footer.vue'
    import MyTop from '../components/top'
    export default {
        components:{
            MyFooter,MyTop
        },
        data(){
            return{
                Regions: [ '金桥开发区', '如意开发区',
                    '玉泉区','回民区','赛罕区','新城区'],
                value: '',
                checkRegions: false,
                checkedRegions: ['新城区'],

                houses:[ '默认', '综合评分由高到低', '成交量由高到低','带看量由高到低'],
                checkedHouses: [''],
            }
        },
        created(){

        },
        methods: {
            CheckAllRegions(val) {
                this.checkRegions = true;
                this.checkedRegions = [""];

            },
            handleCheckedRegionsChange(value) {
                this.checkRegions = false;
            },
            CheckAllPrices(val) {
                this.checkPrices = true;
                this.checkedPrices = [""];

            },
            handleCheckedPricesChange(value) {
                this.checkPrices = false;
            },
        },
        directives:{

        }
    }
</script>
<style>
    .el-checkbox__input.is-checked .el-checkbox__inner,
    .el-checkbox__input.is-indeterminate .el-checkbox__inner {
        background: red;
        border-color: red;
        width: 18px;
        height: 18px;
    }
    .el-checkbox__input.is-focus{
        border: #ddd;
    }
    .el-checkbox__inner{
        width: 18px;
        height: 18px;
        border-color: #ddd;
    }
    .el-checkbox__inner::after{
        box-sizing: content-box;
        content: "";
        border: 3px solid #fff;
        border-left: 0;
        border-top: 0;
        height: 9px;
        left: 5px;
        position: absolute;
        top: 1px;
        -webkit-transform: rotate(45deg) scaleY(0);
        transform: rotate(45deg) scaleY(0);
        width: 3px;
    }
    .el-checkbox__inner:hover{
        border-color: #ddd;
    }
    .el-checkbox__label{
        color: #aaa;
    }
    .el-checkbox__input.is-checked+.el-checkbox__label {
        color: #aaa;
    }
</style>
<style scoped lang="less">
    a{
        text-decoration: none;
    }
    input{
        outline:none;
    }
    .SH-content{
        width: 100%;
        background: white;
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
                    width: 520px;
                }
                #map-btn1{
                    outline: none;
                    margin:  0;
                    height: 58px;
                    width: 165px;
                    border: none;
                    background: brown;
                    font-size: 18px;
                    color: white;
                    border-radius: 3px;
                }
                #map-btn2{
                    outline: none;
                    margin:  0 0 0 18px;
                    height: 58px;
                    width: 165px;
                    border: none;
                    background: blueviolet;
                    font-size: 18px;
                    color: white;
                    border-radius: 3px;
                }

            }
            .top{
                width: 1100px;
                margin: 0 auto;
                padding-bottom: 8px;
                border-bottom: 1px solid #ccc;
                .region{
                    height: 78px;
                    margin: 25px 0 10px 0;
                    .region-tt {
                        float: left;
                        width: 100px;
                        font-size: 14px;
                        padding: 8px 0;
                    }
                    .region-ct {
                        line-height: 38px;
                        float: left;
                        height: 78px;
                        width: 560px;
                        .region-part{
                            font-size: 14px;
                            margin: 0 30px 0 0;
                            .el-icon-check{
                                color: #fff;
                                border: 1px solid #bbb;
                            }
                            .chinese{
                                margin: 0 0 0 12px;
                                color: #888;
                            }
                            span:active{
                                background: red;
                                border: 1px solid red;
                            }
                        }
                        .region-ele{
                            color: #888;
                            margin: 0 28px 0 0 ;
                        }
                    }
                }
                .house{
                    height: 39px;
                    margin: 25px 0 10px 0;
                    .house-tt {
                        float: left;
                        width: 100px;
                        font-size: 14px;
                        padding: 8px 0;
                    }
                    .house-ct {
                        line-height: 38px;
                        float: left;
                        height: 39px;
                        width: 660px;
                        .house-part{
                            font-size: 14px;
                            margin: 0 30px 0 0;
                            .el-icon-check{
                                color: #fff;
                                border: 1px solid #bbb;
                            }
                            .room{
                                margin: 0 0 0 12px;
                                color: #888;
                            }
                            span:active{
                                background: red;
                                border: 1px solid red;
                            }
                        }
                    }
                }
            }
        }
        .resource{
            width: 1100px;
            margin: 75px auto 0 auto;
            .find{
                margin: 20px 0 20px 0;
                color: #222;
                font-size: 30px;
                span{
                    color: red;
                }
            }
            .specific{
                margin-top: 40px;
                height: 135px;
                border-bottom: 1px solid #ccc;
                img{
                    float: left;
                    height: 104px;
                    width: 105px;
                    border-radius: 50%;
                    vertical-align: middle;
                }
                .photo{
                    float: left;
                    width: 370px;
                    padding: 7px 30px;
                    font-size: 16px;
                    color: #000;
                    #address{
                        margin-bottom: 20px;
                    }
                }
                .rank{
                    float: left;
                    width: 200px;
                    height: 100px;
                    padding: 7px 0;
                    text-align: center;
                    #rank-test1{
                        color: red;
                        font-size: 21px;
                        margin-bottom: 20px;
                    }
                    #rank-test2{
                        color: #333;
                        font-size: 16px;
                        margin-bottom: 20px;
                    }
                }
                .phone{
                    padding: 7px 0;
                    float: left;
                    width: 365px;
                    height: 100px;
                    color: #000;
                    text-align: right;
                    #phone-meter1{
                        font-size: 20px;
                        font-weight: 400;
                        margin-bottom: 20px;
                    }
                    #phone-meter2{
                        font-size: 16px;
                        margin-bottom: 20px;
                    }
                }
            }
            .page{
                text-align: right;
                height: 105px;
                margin: 50px 0 40px 0 ;
                span{
                    color: #888;
                    border: 1px solid #ccc;
                    border-radius: 3px;
                    margin: 0 3px;
                    padding:10px 15px;
                    cursor: pointer;
                }
            }
        }

    }

</style>