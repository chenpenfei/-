<template>
    <div>
        <my-top2/>
        <encyAnd/>

        <div class="content">
            <div class="title-top">
                <div id="sun">福居网> 二手房 >采光好</div>
                <div id="share">
                    <span><i class="el-icon-star-off"></i>关注此房源</span>
                    <span><i class="el-icon-share"></i>分享此房源</span>
                </div>
            </div>

            <div class="lighting">
                <h3>采光好</h3>

                <div class="vue-zoom-container"
                     v-scale="{options: currentOptions,url: minUrl}" ref="scaleBox">

                    <div class="vue-zoom-min-box _leftBox" >
                        <img src="../assets/img/pic1.png"  class="_minPic">
                        <div class="_vue-mask"></div>
                    </div>

                    <div class="vue-zoom-max-box _rightBox"  >
                        <img src="../assets/img/pic1.png"  class="_maxPic">

                    </div>

                    <div class="right-box">
                        <div class="price-box box">
                            <div class="price-left left">
                                <span type="1">49</span>
                                <span>万</span>
                            </div>
                            <div class="price-right right">
                                <div type>7923 元/平米 </div>
                                <div>首付 待定</div>
                            </div>
                        </div>
                        <div class="floor-box box">
                            <div class="fll-left left">
                                <div type>1室1厅</div>
                                <div>中楼层/6层</div>
                            </div>
                            <div class="fll-left">
                                <div type>西</div>
                                <div>简装/</div>
                            </div>
                            <div class="fll-right">
                                <div type>60.58平米</div>
                                <div>0年建/平层</div>
                            </div>
                        </div>
                        <div class="resource-box box">
                            <div class="resource left">
                                <div class="floor">房源编号 :  <span>syq82216</span></div>
                                <div>所在区域 :</div>
                            </div>
                            <div class="resource right">
                                <div class="floor">小区名称 : <span>宏丰小区</span></div>
                                <div>看房时间 : </div>
                            </div>
                        </div>
                        <div class="name-box box">
                            <a href="" class="left">
                                <img src="../assets/img/seach-2.png"
                                     style="height: 82px;width: 82px;border-radius: 50%">
                            </a>
                            <div class="name-name left">
                                <div type="name">赵秀芳</div>
                                <div type="age">从业年限 :  2年</div>
                                <div type="phone">400-898-1018 转 3111</div>
                            </div>
                            <div class="name-dis right">
                                评分 :  5.0/ 0人评价
                            </div>
                        </div>
                        <div class="btn-box">预约看房</div>
                    </div>
                </div>

                <div class="switch-box">
                    <div class="switch fll-left" @click="handlePrev">
                        <i class="el-icon-arrow-left"></i>
                    </div>

                    <div class="switch-box-wrap fll-left">
                        <ul class="switch-box clearfix">
                            <li class="switch-item"
                                v-for="(item,index) in imgData">
                                <img :src="'http://www.fooju.cn'+item.pic">
                            </li>

                            <li class="active" ></li>
                        </ul>
                    </div>

                    <div class="switch fll-left" @click="handleNext">
                        <i class="el-icon-arrow-right"></i>
                    </div>
                </div>

            </div>

            <div class="message">
                <h2>基本信息</h2>
                <div>
                    <div>房屋户型 :  1室1厅1卫 所在楼层 :  中楼层/6</div>
                    <div>建筑面积 :  60.58㎡ 房屋类型 :  商住两用</div>
                    <!--<div>套内面积 :  58.00㎡ 建筑类型 :  {{msgData.jibenxinxi.type}}</div>-->
                    <div>房屋朝向 :  西 建筑结构 :</div>
                    <div>装修情况 :  简装 梯户比例 :</div>
                    <div>产权年限 :  70年 配备电梯 :</div>
                    <div>交通情况 :  62，83 产权性质 :</div>
                    <div>挂牌时间 :  2018-07-12 建造年代 :  0年</div>
                </div>
            </div>
            <div class="feature">
                <h2>房源特色</h2>
                <div>
                    <div>房源标签 :</div>
                    <div>核心卖点 :  地段繁华</div>
                    <div>户型介绍 :  朝北</div>
                    <div>小区介绍 :  小区环境好</div>
                    <div>周边配套 :  周边配套齐全</div>
                </div>
            </div>
            <div class="picture">
                <h2>房源照片</h2>
                <div>
                    <div></div>
                    <div></div>
                </div>
            </div>
            <div class="assort">
                <h2>周边配套</h2>
            </div>
        </div>

        <my-footer/>
    </div>
</template>

<script>
    import MyFooter from '~/components/Footer.vue'
    import MyTop2 from '../components/top2'
    import encyAnd from '../components/encyandtwo.vue'
    import api from '~/mainApi/index'
    import axios from '~/plugins/axios'
    import {mapState,mapMutations} from 'vuex'
    export default {
        name: "secondDetails",
        layout: "secondHandDetails",
        components:{
            MyFooter,MyTop2,encyAnd
        },
        async asyncData(){

        },
        data() {
            return {
                currentOptions: this.options,
                currentUrl: this.minUrl,
                houseData:{},
                queryId:{
                    id:this.$route.params.id
                },
                translate: "(0,0)",
                left: 0,
                detailData:[
                    {agent_lists:""},
                    {angyuanzhaopian:""},
                    {jibenxinxi:""},
                    {jingjirenpingfang:""},
                    {kanfangjilu:""},
                    {tongxiaoquchengjiao:""},
                ],
                imgData:[]
            }
        },
        methods: {
            getData() {
                axios.get(api.paramToUrl(api.used_detail, {id:this.$route.query.id})).then(res => {
                    // console.log(res.data.data.jibenxinxi.pic);
                    this.detailData = res.data.data;
                    this.imgData = res.data.data.jibenxinxi.pic;
                    console.log(this.imgData);
                    // console.log(this.detailData);
                    // this.dataArr(res.data.data);
                })
            },

            handlePrev(){
                let index = this.currentHouseIndex - 1;
                if(index>this.maxIndex){
                    this.setCurrentHouse(index);
                }
                else if(index<0){
                    this.setCurrentHouse(this.houseDetails.jibenxinxi.pic.length-1);
                    this.translate = `(${-this.maxIndex*130}px,0)`
                }
                else {
                    this.setCurrentHouse(index)
                    this.translate = `(${-index*130}px,0)`
                }
            },
            handleNext(){
                let index = this.currentHouseIndex + 1;
                if(index>this.maxIndex){
                    if(index>this.houseDetails.jibenxinxi.pic.length-1){
                        this.setCurrentHouse(0);
                        this.translate = `(${-0*130}px,0)`
                    }
                    else {
                        this.setCurrentHouse(index);
                    }
                }
                else {
                    this.setCurrentHouse(index);
                    this.translate = `(${-index*130}px,0)`
                }
            },
            ...mapMutations(["setHouseDetails"])
        },
        created(){
            this.getData();
            // console.log(this.queryId);
        },
        props: {
            options: {
                type: Object
            },
            minUrl: {
                type: String
            },
        },
        computed:{
            maxIndex() {
                return this.houseDetails.jibenxinxi.pic.length-4;
            },
            currentLeft() {
                return this.currentHouseIndex*130;
            },
            ...mapState(["houseDetails","currentHouseIndex"])
        },
        directives: {
            scale: {
                inserted(el,binding,vnode){
                    // console.log(binding.value)
                    let leftBox = el.querySelector("._leftBox");
                    let minPic = el.querySelector("._minPic");
                    let mask = el.querySelector("._vue-mask");
                    let maxPic = el.querySelector("._maxPic");
                    let rightBox = el.querySelector("._rightBox");

                    // maxPic.src = minPic.src = binding.value.url;

                    function mouseIn(ev) {
                        ev = ev || event;

                        document.addEventListener("mousemove",mouseMove)
                        leftBox.addEventListener("mouseleave",mouseLeave)
                    }
                    function mouseMove(ev){
                        ev = ev || event;
                        let scrollTop = document.documentElement.scrollTop || document.body.scrollTop;
                        let computedLeft = ev.clientX - el.offsetLeft - mask.offsetWidth/2;
                        let computedTop = ev.clientY - el.offsetTop + scrollTop - mask.offsetHeight/2;
                        let limitLeft = leftBox.offsetWidth-mask.offsetWidth;
                        let limitTop = leftBox.offsetHeight-mask.offsetHeight
                        mask.style.display = "block";


                        if(computedLeft<0){
                            computedLeft = 0;
                        }
                        else if(computedLeft>limitLeft){
                            computedLeft = limitLeft
                        }

                        if(computedTop<0){
                            computedTop = 0;
                        }
                        else if (computedTop>limitTop){
                            computedTop = limitTop;
                        }
                        mask.style.top = computedTop + "px";
                        mask.style.left = computedLeft + "px";
                        rightBox.style.display = "block";
                        maxPic.style.transform= `translate3d(${-computedLeft*2.5}px,${-computedTop*2.5}px,0)`

                    }
                    function mouseLeave(ev) {
                        ev = ev || event;
                        document.removeEventListener("mousemove", mouseMove)
                        mask.style.display = "none";
                        rightBox.style.display = "none"
                    }

                    el._move = mouseMove;
                    el._in = mouseIn;
                    el._leave = mouseLeave;
                    leftBox.onmouseenter = mouseIn

                },
                unbind(el,binding,vnode){
                    let leftBox = el.querySelector("._leftBox");
                    let minPic = el.querySelector("._minPic");
                    let mask = el.querySelector("._vue-mask");
                    let maxPic = el.querySelector("._maxPic");
                    let rightBox = el.querySelector("._rightBox");

                    leftBox.removeEventListener("mouseenter",el._in);
                }
            }
        },
        watch: {
            options(val,old) {
                this.currentOptions = val;
                // console.log(this)
            },
            minUrl(val) {
                this.currentUrl = val;
            }
        }
    }
</script>

<style scoped lang="less">

    .content{
        width: 1100px;
        margin: 0 auto;
        .title-top{
            margin: 15px 0 20px 0;
            height: 30px;
            line-height: 30px;
            font-size: 14px;
            color: #999999;
            #sun {
                float: left;
            }
            #share {
                cursor: pointer;
                float: right;
                span{
                    margin-left: 30px;
                    i{
                        margin-right: 6px;
                    }
                }
            }
        }
        .lighting{
            h3{
                margin: 20px 0;
                font-size: 33px;
                color: #000;
            }
            .vue-zoom-container {
                position: relative;
                .vue-zoom-min-box {
                    position: relative;
                    width: 592px;
                    height: 442px;
                    overflow: hidden;
                    img {
                        display: block;
                        width: 100%;
                        height: 100%;
                    }
                    ._vue-mask {
                        position: absolute;
                        cursor: move;
                        width: 237px;
                        height: 216px;
                        background: rgba(255,255,0,.2);
                    }
                }
                .vue-zoom-max-box {
                    z-index: 800;
                    display: none;
                    position: absolute;
                    left: 55%;
                    top: 0;
                    width: 592px;
                    height: 542px;
                    overflow: hidden;
                    img{
                        display: block;
                        width: 1480px;
                        height: 1105px
                    }
                }
                .right-box{
                    width: 480px;
                    position: absolute;
                    left: 56%;
                    top: 0;
                    .box{
                        margin-top: 30px;
                        padding-bottom: 30px;
                        border-bottom: 1px solid #ccc;
                    }
                    .box:after{
                        content:".";
                        height:0;
                        visibility:hidden;
                        display:block;
                        clear:both;
                    }
                    .left{
                        float: left;
                    }
                    .right{
                        float: right;
                    }
                    .price-box{
                        color: #000;
                        font-size: 14px;
                        .price-left{
                            font-size: 20px;
                            color: #c30d23;
                            span[type="1"]{
                                font-size: 40px;
                            }
                        }
                        .price-right div[type]{
                            margin-bottom: 5px;
                        }
                    }
                    .floor-box{
                        font-size: 14px;
                        color: #888;
                        .fll-left{
                            text-align: center;
                            float: left;
                            div[type]{
                                margin-bottom: 6px;
                                font-size: 20px;
                                color: #333;
                            }
                        }
                        .fll-right{
                            text-align: center;
                            float: right;
                            div[type]{
                                margin-bottom: 6px;
                                font-size: 20px;
                                color: #333;
                            }
                        }
                        .left{
                            margin-right: 150px;
                        }
                    }
                    .resource-box {
                        font-size: 14px;
                        color: #888;
                        .resource {
                            .floor{
                                margin-bottom: 16px;
                                span{
                                    color: #333;
                                }
                            }
                        }
                    }
                    .name-box{
                        border: none;
                        .name-name{
                            margin-left: 20px;
                            div[type="name"]{
                                font-size: 24px;
                                color: #333;
                                margin-bottom: 20px;
                            }
                            div[type="age"]{
                                font-size: 14px;
                                color: #333;
                                margin-bottom: 20px;
                            }
                            div[type="phone"]{
                                font-size: 20px;
                                color: #c30d23;
                            }
                        }
                        .name-dis{
                            color: #333;
                            font-size: 14px;
                        }
                    }
                    .btn-box{
                        text-align: center;
                        float: right;
                        width: 100px;
                        height: 48px;
                        line-height: 48px;
                        font-size: 16px;
                        color: #c30d32;
                        border: 1px solid #c30d32;
                        padding: 0 30px;
                        border-radius: 4px;
                    }
                    .btn-box:hover{
                        cursor: pointer;
                        color: #fff;
                        background: #c30d32;
                    }
                }
            }
            .switch-box{
                width: 598px;
                height: 90px;
                .switch{
                    margin-top: 10px;
                    height: 90px;
                    line-height: 90px;
                    width: 29px;
                    border: 1px solid #5f1985;
                    i{
                        font-size: 30px;
                    }
                }
                .switch:hover{
                    color: #fff;
                    background: #5f1985;
                }

                .switch-box-wrap{
                    position: relative;
                    margin: 0 9px;
                    width: 512px;
                    height: 102px;
                    overflow: hidden;
                    .switch-box {
                        transition: transform ease-in-out .5s;
                        width: 3000px;
                    }
                    .active {
                        position: absolute;
                        z-index: 998;
                        top: 10px;
                        box-sizing: border-box;
                        width: 120px;
                        height: 92px;
                        border: 2px solid #5f1985;
                        &::after {
                            content: "";
                            position: absolute;
                            top: -10px;
                            left: 54px;
                            width: 0;
                            height: 0;
                            border-left: 5px solid transparent;
                            border-right: 5px solid transparent;
                            border-bottom: 10px solid #5f1985;

                        }
                    }
                }
                .switch-item {
                    position: relative;
                    float: left;
                    margin-top: 10px;
                    margin-right: 10px;
                    user-select: none;
                    width: 120px;
                    img {
                        display: block;
                        width: 100%;
                        height: 91px;
                    }
                }
                .fll-left{
                    float: left;
                }
            }
        }
        .message{
            h2{
                margin: 20px 0;
                font-size: 33px;
                color: #000;
            }
        }
        .feature{
            h2{
                margin: 20px 0;
                font-size: 33px;
                color: #000;
            }
        }
        .picture{
            h2{
                margin: 20px 0;
                font-size: 33px;
                color: #000;
            }
        }
        .assort{
            h2{
                margin: 20px 0;
                font-size: 33px;
                color: #000;
            }
        }
    }

</style>