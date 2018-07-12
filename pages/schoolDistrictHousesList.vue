<template>
    <div>
        <my-top2/>
            <div class="SH-content">
                <div class="SH-content-big">
                    <div class="SH-content-title">
                        <img src="../assets/img/logo.png">
                        <span @click="click">呼和浩特
                        <i class="iconfont icon-jiantouxia"></i></span>
                        <a href="">二手房</a>
                        <a href="">新房</a>
                        <a href="">租房</a>
                    </div>
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

                <div class="main">
                    <p>福居网> 学区房-二手房</p>

                    <div class="SH-title-bottom">

                        <div>
                            <input type="text" placeholder="搜索">
                            <button>搜索</button>
                        </div>
                    </div>

                    <div class="top">
                        <div class="region">
                            <div class="region-tt">区域</div>
                            <div class="region-ct">
                                <label class="region-part">
                                    <span class="el-icon-check"></span>
                                    <span class="chinese">不限</span>
                                </label>
                                <el-checkbox class="region-ele">金桥开发区</el-checkbox>
                                <el-checkbox class="region-ele">如意开发区</el-checkbox>
                                <el-checkbox class="region-ele">玉泉区</el-checkbox>
                                <el-checkbox class="region-ele">回民区</el-checkbox>
                                <el-checkbox class="region-ele">赛罕区</el-checkbox>
                                <el-checkbox class="region-ele">新城区</el-checkbox>
                            </div>
                        </div>
                        <div class="price">
                            <div class="price-tt">价格</div>
                            <div class="price-ct">
                                <label class="price-part">
                                    <span class="el-icon-check"></span>
                                    <span class="price-money">不限</span>
                                </label>
                                <el-checkbox class="price-ele">30万以下</el-checkbox>
                                <el-checkbox class="price-ele">30-40万</el-checkbox>
                                <el-checkbox class="price-ele">40-50万</el-checkbox>
                                <el-checkbox class="price-ele">50万以上</el-checkbox>
                                <input type="text" style="width: 60px">
                                - <input type="text" style="width: 60px"> 万
                                <button>确定</button>
                            </div>
                        </div>
                        <div class="house">
                            <div class="house-tt">户型</div>
                            <div class="house-ct">
                                <label class="house-part">
                                    <span class="el-icon-check"></span>
                                    <span class="room">一室</span>
                                </label>
                                <label class="house-part">
                                    <span class="el-icon-check"></span>
                                    <span class="room">二室</span>
                                </label>
                                <label class="house-part">
                                    <span class="el-icon-check"></span>
                                    <span class="room">三室</span>
                                </label>
                                <label class="house-part">
                                    <span class="el-icon-check"></span>
                                    <span class="room">四室</span>
                                </label>
                                <label class="house-part">
                                    <span class="el-icon-check"></span>
                                    <span class="room">五室</span>
                                </label>
                            </div>
                        </div>
                    </div>

                    <div class="middle">
                        <div class="flex-content" style="height: 0;" v-trans>
                            <slot>
                                <div class="region">
                                    <div class="region-tt">区域</div>
                                    <div class="region-ct">
                                        <label class="region-part">
                                            <span class="el-icon-check"></span>
                                            <span class="chinese">不限</span>
                                        </label>
                                        <el-checkbox class="region-ele">金桥开发区</el-checkbox>
                                        <el-checkbox class="region-ele">如意开发区</el-checkbox>
                                        <el-checkbox class="region-ele">玉泉区</el-checkbox>
                                        <el-checkbox class="region-ele">回民区</el-checkbox>
                                        <el-checkbox class="region-ele">赛罕区</el-checkbox>
                                        <el-checkbox class="region-ele">新城区</el-checkbox>
                                    </div>
                                </div>
                                <div class="price">
                                    <div class="price-tt">价格</div>
                                    <div class="price-ct">
                                        <label class="price-part">
                                            <span class="el-icon-check"></span>
                                            <span class="price-money">不限</span>
                                        </label>
                                        <el-checkbox class="price-ele">30万以下</el-checkbox>
                                        <el-checkbox class="price-ele">30-40万</el-checkbox>
                                        <el-checkbox class="price-ele">40-50万</el-checkbox>
                                        <el-checkbox class="price-ele">50万以上</el-checkbox>
                                        <input type="text" style="width: 60px">
                                        - <input type="text" style="width: 60px"> 万
                                        <button>确定</button>
                                    </div>
                                </div>
                            </slot>
                        </div>
                    </div>

                    <div class="screen">
                        <slot>
                            <div class="screen-title">筛选分类</div>
                            <div class="screen-content">
                                <div class="screen-item">
                                    回民区
                                    <i class="iconfont icon-cha"></i>
                                </div>
                                <div class="screen-clear">
                                    <i class="iconfont icon-lajitong"></i>
                                    清除全部
                                </div>
                            </div>
                        </slot>
                    </div>

                    <div class="more-btn"  @click="handleShow">
                        {{isShow?"更多选项":"收起选项"}}
                        <i class="iconfont icon-jiantoushang" v-if="isShow"></i>
                        <i class="iconfont icon-jiantouxia" v-else="isShow"></i>
                    </div>

                </div>

                <div class="resource">

                    <div class="rank">
                        <span>最新</span>
                        <span class="room">房屋总价 <i class="iconfont icon-jiantou1-copy-copy"></i></span>
                        <span class="room">房屋单价 <i class="iconfont icon-jiantou1-copy-copy"></i></span>
                        <span class="room">房屋面积 <i class="iconfont icon-jiantou1-copy-copy"></i></span>
                    </div>

                    <div class="find">
                        共找到
                        <span>186</span>套
                        <span style="color: #000"> 呼和浩特
                        </span>二手房源
                    </div>

                    <div class="specific">
                        <img src="../assets/img/家居图.png">
                        <div class="address">
                            <div id="address-test">紧挨石东路小学</div>
                            <p>
                                <span>绿缘小区</span>
                                <span> | 2室1厅1卫</span>
                                <span> | 东西</span>
                            </p>
                            <p>
                                <span>高楼层/6层</span>
                                <span> | 简装</span>
                            </p>
                            <p>
                                <span>1995年建</span>
                                <span> | 多层</span>
                            </p>
                            <p>
                                <span>0人关注</span>
                                <span> | 共 0次带看</span>
                                <span> | 今天发布</span>
                            </p>
                        </div>
                        <div class="cost">
                            <div id="cost-money">
                                <span style="color: #c30d23;font-size: 40px">49</span>
                                <span style="color: #c30d23;font-size: 22px">万</span>
                            </div>
                            <div id="cost-meter">单价 7890元/平米</div>
                            <div href="" id="cost-attention">关注</div>
                        </div>
                    </div>
                    <div class="specific">
                        <img src="../assets/img/家居图.png">
                        <div class="address">
                            <div id="address-test">紧挨石东路小学</div>
                            <p>
                                <span>绿缘小区</span>
                                <span> | 2室1厅1卫</span>
                                <span> | 东西</span>
                            </p>
                            <p>
                                <span>高楼层/6层</span>
                                <span> | 简装</span>
                            </p>
                            <p>
                                <span>1995年建</span>
                                <span> | 多层</span>
                            </p>
                            <p>
                                <span>0人关注</span>
                                <span> | 共 0次带看</span>
                                <span> | 今天发布</span>
                            </p>
                        </div>
                        <div class="cost">
                            <div id="cost-money">
                                <span style="color: #c30d23;font-size: 40px">49</span>
                                <span style="color: #c30d23;font-size: 22px">万</span>
                            </div>
                            <div id="cost-meter">单价 7890元/平米</div>
                            <div href="" id="cost-attention">关注</div>
                        </div>
                    </div>
                    <div class="specific">
                        <img src="../assets/img/家居图.png">
                        <div class="address">
                            <div id="address-test">紧挨石东路小学</div>
                            <p>
                                <span>绿缘小区</span>
                                <span> | 2室1厅1卫</span>
                                <span> | 东西</span>
                            </p>
                            <p>
                                <span>高楼层/6层</span>
                                <span> | 简装</span>
                            </p>
                            <p>
                                <span>1995年建</span>
                                <span> | 多层</span>
                            </p>
                            <p>
                                <span>0人关注</span>
                                <span> | 共 0次带看</span>
                                <span> | 今天发布</span>
                            </p>
                        </div>
                        <div class="cost">
                            <div id="cost-money">
                                <span style="color: #c30d23;font-size: 40px">49</span>
                                <span style="color: #c30d23;font-size: 22px">万</span>
                            </div>
                            <div id="cost-meter">单价 7890元/平米</div>
                            <div href="" id="cost-attention">关注</div>
                        </div>
                    </div>
                    <div class="specific">
                        <img src="../assets/img/家居图.png">
                        <div class="address">
                            <div id="address-test">紧挨石东路小学</div>
                            <p>
                                <span>绿缘小区</span>
                                <span> | 2室1厅1卫</span>
                                <span> | 东西</span>
                            </p>
                            <p>
                                <span>高楼层/6层</span>
                                <span> | 简装</span>
                            </p>
                            <p>
                                <span>1995年建</span>
                                <span> | 多层</span>
                            </p>
                            <p>
                                <span>0人关注</span>
                                <span> | 共 0次带看</span>
                                <span> | 今天发布</span>
                            </p>
                        </div>
                        <div class="cost">
                            <div id="cost-money">
                                <span style="color: #c30d23;font-size: 40px">49</span>
                                <span style="color: #c30d23;font-size: 22px">万</span>
                            </div>
                            <div id="cost-meter">单价 7890元/平米</div>
                            <div href="" id="cost-attention">关注</div>
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
    import MyTop2 from '../components/top2'
    export default {
        components:{
            MyFooter,MyTop2
        },
        data(){
            return{
                checkList: ['选中且禁用','复选框 A'],
                isShow:false,
                show:"",
            }
        },
        created(){

        },
        methods: {
                handleShow(isShow){
                    this.isShow = !this.isShow;
                },
                click(){
                    this.show = true
                },
                back(){
                    this.show = false
                },
        },
        directives:{
            trans:{
                update(el,biding,vnode){
                    let isShow = vnode.context.$data.isShow;
                    if(!isShow){
                        el.style.height = 0;
                    }else{
                        el.style.height = "auto";
                        let startHeight = 0;
                        let targetHeight = getComputedStyle(el).height;
                        el.style.height= 0;
                        el.style.height = startHeight;
                        el.offsetWidth;
                        el.style.transition = "height ease .5s";
                        el.style.height = targetHeight;
                    }
                }
            }
        }
    }
</script>
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
    .SH-content-big{
        width: 100%;
        border-bottom: 1px solid #ccc;
        .SH-content-title{
            height: 80px;
            line-height: 80px;
            width: 1100px;
            margin: 0 auto;
            background: white;
            span {
                padding: 6px;
                margin: 0 0 0 10px;
                border: 1px solid #999;
                border-radius: 25px;
                .iconfont {
                    vertical-align: middle;
                    font-size: 16px;
                }
            }
            img{
                vertical-align: middle;
                margin-right: 20px;
            }
            a{
                font-size: 16px;
                color: black;
                margin: 0 0 0 40px;
            }
            a:hover{
                color: red;
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
        #content{
            margin: 0 40px;
        }
        #back{
            margin: 8px 8px 0 0;
            color: #7f828b;
            font-size: 28px;
            text-align: right;
        }
        h2{
            font-size: 22px;
            color: #333;
            padding: 0  0 8px 0;
            border-bottom: 1px solid #7f828b;
        }
        p{
            font-size: 18px;
            margin: 20px 0;
        }
        li{
            list-style-type:none;
            margin: 5px 0;
        }
    }
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
        .top{
            width: 1100px;
            margin: 0 auto;
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
            .price{
                height: 78px;
                margin: 25px 0 10px 0;
                .price-tt {
                    float: left;
                    width: 100px;
                    font-size: 14px;
                    padding: 8px 0;
                }
                .price-ct{
                    line-height: 38px;
                    float: left;
                    height: 78px;
                    width: 560px;

                    .price-part{
                        font-size: 14px;
                        margin: 0 30px 0 0;
                        .el-icon-check{
                            color: #fff;
                            border: 1px solid #bbb;
                        }
                        .price-money{
                            margin: 0 0 0 12px;
                            color: #888;
                        }
                        span:active{
                            background: red;
                            border: 1px solid red;
                        }
                    }
                    .price-ele{
                        color: #888;
                        margin: 0 30px 0 0;
                    }
                    button{
                        width: 50px;
                        height: 26px;
                        background: #c30d23;
                        border: none;
                        color: #fff;
                        font-size: 14px;
                        margin-left: 10px
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
                    width: 560px;
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
        .middle{
            width: 1100px;
            margin: 0 auto;
            .flex-content{
                transition: height ease .3s;
                overflow: hidden;
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
                .price{
                    height: 78px;
                    margin: 25px 0 10px 0;
                    .price-tt {
                        float: left;
                        width: 100px;
                        font-size: 14px;
                        padding: 8px 0;
                    }
                    .price-ct{
                        line-height: 38px;
                        float: left;
                        height: 78px;
                        width: 560px;

                        .price-part{
                            font-size: 14px;
                            margin: 0 30px 0 0;
                            .el-icon-check{
                                color: #fff;
                                border: 1px solid #bbb;
                            }
                            .price-money{
                                margin: 0 0 0 12px;
                                color: #888;
                            }
                            span:active{
                                background: red;
                                border: 1px solid red;
                            }
                        }
                        .price-ele{
                            color: #888;
                            margin: 0 30px 0 0;
                        }
                        button{
                            width: 50px;
                            height: 26px;
                            background: #c30d23;
                            border: none;
                            color: #fff;
                            font-size: 14px;
                            margin-left: 10px
                        }
                    }
                }
            }
        }
        .screen {
            width: 1100px;
            height: auto;
            margin: 10px auto;
            .screen-title {
                float: left;
                width: 100px;
                font-size: 14px;
                padding: 8px 0;
                margin: 10px 0;
            }
            .screen-content{
                margin: 10px 0;
                width: 700px;
                float: left;
                .screen-item{
                    height: 28px;
                    line-height: 28px;
                    float: left;
                    border: 1px solid #ccc;
                    padding: 0 0 0 20px;
                    .iconfont{
                        background: #ccc;
                        margin-left: 16px;
                        padding: 6px;
                        color: #ffffff;
                    }
                }
                .screen-clear {
                    margin-left: 30px;
                    float: left;
                    width: 100px;
                    font-size: 14px;
                    padding: 8px 0;
                    .iconfont {
                        font-size: 20px;
                    }
                }
            }

        }
        .more-btn{
            clear: both;
            text-align: center;
            font-size: 16px;
            color: #7f828b;
            width: 1100px;
            padding: 25px 0;
            margin: 20px auto;
            border-bottom: 1px solid #ccc;
        }
    }
    .resource{
        width: 1100px;
        margin: 100px auto 0 auto;
        .rank{
            cursor: pointer;
            height: 42px;
            span{
                color: #fff;
                font-size: 18px;
                background: #c30d23;
                padding: 10px 20px;
                border-radius: 20px;
            }
            .room{
                margin-left: 24px;
                color: #c30d23;
                font-size: 18px;
                background: #fff;
                padding: 8px 20px;
                border-radius: 30px;
                border: 1px solid #c30d23;
            }
            .room:hover{
                background:#c30d23;
                color: #fff;
            }
        }
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
            height: 217px;
            img{
                float: left;
                height: 214px;
                width: 285px;
            }
            .address{
                float: left;
                width: 605px;
                height: 214px;
                padding: 0 30px;
                #address-test{
                    color: #333;
                    font-size: 20px;
                    margin-bottom: 30px;
                }
                p{
                    margin: 17px 0;
                }
            }
            .cost{
                float: left;
                width: 150px;
                height: 214px;
                text-align: right;
                #cost-money{
                    margin-bottom: 10px
                }
                #cost-meter{
                    margin: 20px 0;
                    color: #555;
                    font-size: 14px;
                }
                #cost-attention{
                    cursor: pointer;
                    color: #c30d23 ;
                    float: right;
                    text-align: center;
                    font-size: 16px;
                    margin: 20px 0;
                    padding: 10px 0;
                    width: 100px;
                    border: 1px solid #c30d23;
                    border-radius: 5px;
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