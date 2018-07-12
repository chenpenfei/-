<template>
    <div>
        <my-top2/>
        <div class="SH-content">

            <ency-and/>
            <Seach/>

            <div class="sum">
                <div class="classify">
                    <h2>百科分类</h2>

                    <div class="second">
                        <div class="title">二手房</div>
                        <div class="part">
                            <div class="buy">
                                <a href="">卖房风险</a>
                            </div>
                            <div class="buy">
                                <a href="">入住/交接</a>
                            </div>
                            <div class="buy"><a href="">缴税/过户</a></div>
                            <div class="buy"><a href="">全款/贷款</a></div>
                            <div class="buy"><a href="">卖房风险</a></div>
                            <div class="buy"><a href="">签约/定房</a></div>
                            <div class="buy"><a href="">看房/选房</a></div>
                            <div class="buy"><a href="">准备买房</a></div>
                        </div>
                    </div>
                    <div class="second">
                        <div class="title">新房</div>
                        <div class="part">
                            <div class="buy"><a href="">认购新房</a></div>
                            <div class="buy"><a href="">看房/选房 </a></div>
                            <div class="buy"><a href="">活动</a></div>
                            <div class="buy"><a href="">签约/定房</a></div>
                            <div class="buy"><a href="">收房/验房</a></div>
                            <div class="buy"><a href="">装修/入住</a></div>
                            <div class="buy"><a href="">看房/选房</a></div>
                            <div class="buy"><a href="">房产活动</a></div>
                            <div class="buy"><a href="">网签数据</a></div>
                        </div>
                    </div>
                    <div class="second">
                        <div class="title">购房宝典</div>
                        <div class="part">
                            <div class="buy"><a href="">房产政策</a></div>
                            <div class="buy"><a href="">购房建议</a></div>
                            <div class="buy"><a href="">法律纠纷</a></div>
                        </div>
                    </div>
                    <div class="second">
                        <div class="title">租房</div>
                        <div class="part">
                            <div class="buy"><a href="">注意事项</a></div>
                            <div class="buy"><a href="">租房风险</a></div>
                        </div>
                    </div>
                    <div class="second">
                        <div class="title">换房</div>
                        <div class="part">
                            <div class="buy"><a href="">准备换房</a></div>
                            <div class="buy"><a href="">换房风险</a></div>
                            <div class="buy"><a href="">缴税/过户</a></div>
                        </div>
                    </div>

                </div>

                <div class="risk">
                        <h2>买房风险</h2>
                        <div id="line"></div>
                        <a href="">
                            <div class="clever">
                                <img src="../assets/img/buyhouse.jpg" alt="">
                                <div class="news">
                                    <div class="topic">买房遇到这种阳台的户型，再便宜聪明人都不会买，有钱人一看就懂</div>
                                    <div class="details">买房遇到这种阳台的户型，再便宜聪明人都不会买，有钱人一看就懂</div>
                                    <div class="time">2018-06-25 17:50:58</div>
                                </div>
                            </div>
                        </a>
                        <a href="">
                            <div class="clever">
                                <img src="../assets/img/buyhouse.jpg" alt="">
                                <div class="news">
                                    <div class="topic">买房遇到这种阳台的户型，再便宜聪明人都不会买，有钱人一看就懂</div>
                                    <div class="details">买房遇到这种阳台的户型，再便宜聪明人都不会买，有钱人一看就懂</div>
                                    <div class="time">2018-06-25 17:50:58</div>
                                </div>
                            </div>
                        </a>
                </div>
            </div>

            <Pages/>

        </div>
        <my-footer/>
    </div>
</template>
<script>
    import MyFooter from '~/components/Footer.vue'
    import MyTop2 from '../components/top2'
    import encyAnd from '../components/encyand.vue'
    import Seach from '../components/seach.vue'
    import Pages from '../components/pages.vue'
    export default {
        components:{
            MyFooter,MyTop2,encyAnd,Seach,Pages
        },
        data(){
            return {

            }
        },
        created(){

        },

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
        .sum{
            clear: both;
            width: 1100px;
            margin: 100px auto 0 auto;
            .classify{
                width: 300px;
                float: left;
                margin-right: 100px;
                h2{
                    font-size: 32px;
                    font-weight: 600;
                    color: #000;
                    padding-bottom: 20px;
                    border-bottom: 1px solid #bbb;
                }
                .second{
                    clear: both;
                    margin: 20px 0 20px 0;
                    .title{
                        font-size: 22px;
                        font-weight: 800;
                        color: #333;
                        margin: 10px 0;
                    }
                    .part{
                        overflow:auto; zoom:1;
                        margin-bottom: 45px;
                        .buy{
                            float: left;
                            color: #444;
                            margin: 7px 0;
                            width: 99px;
                        }
                    }
                }

            }
            .risk{
                width: 700px;
                float: left;
                h2{
                    font-size: 32px;
                    font-weight: 600;
                    color: #000;
                    padding-bottom: 20px;
                    border-bottom: 1px solid #bbb;
                }
                #line{
                    width: 700px;
                    height: 20px;
                }
                .clever{
                    margin-top: 20px;
                    width: 700px;
                    height: 210px;
                    img{
                        width: 280px;
                        height: 210px;
                    }
                    .news{
                        width: 390px;
                        margin-left: 30px;
                        float: right;
                        .topic{
                            font-size: 20px;
                            color: #333;
                            cursor: pointer;
                        }
                        .details{
                            font-size: 14px;
                            color: #333;
                            margin: 25px 0;
                            line-height: 2;
                        }
                        .time{
                            font-size: 14px;
                            color: #999;
                        }
                    }
                }
            }
        }


    }

</style>