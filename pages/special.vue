<template>
    <div>
        <my-top2/>
        <encyAnd/>
        <Seach/>
        <div class="hot">
            <div class="hot-title">热门</div>

            <img src="../assets/img/shengxia.jpg" alt="">
            <div class="images">
                <img src="../assets/img/shengxia.jpg" class="img-one">
                <img src="../assets/img/shengxia.jpg" class="img-two">
                <img src="../assets/img/shengxia.jpg" class="img-three">
                <img src="../assets/img/shengxia.jpg" class="img-four">
            </div>

        </div>
        <div class="active">
            <div class="active-title">
                <div class="active-active">活动</div>
                <div class="active-more">更多 ></div>
            </div>
            <div class="line"></div>

            <div class="active-news">
                <div class="active-content">10月迫啊死哦点击</div>
                <div class="active-date">2017-2-5</div>
            </div>
            <div class="active-news">
                <div class="active-content">10月迫啊死哦点击</div>
                <div class="active-date">2017-2-5</div>
            </div>
        </div>
        <div class="active">
            <div class="active-title">
                <div class="active-active">楼盘</div>
                <div class="active-more">更多 ></div>
            </div>
            <div class="line"></div>

            <div class="active-news">
                <div class="active-content">10月迫啊死哦点击</div>
                <div class="active-date">2017-2-5</div>
            </div>
            <div class="active-news">
                <div class="active-content">10月迫啊死哦点击</div>
                <div class="active-date">2017-2-5</div>
            </div>
        </div>
        <div class="active">
            <div class="active-title">
                <div class="active-active">二手房</div>
                <div class="active-more">更多 ></div>
            </div>
            <div class="line"></div>

            <div class="active-news">
                <div class="active-content">10月迫啊死哦点击</div>
                <div class="active-date">2017-2-5</div>
            </div>
            <div class="active-news">
                <div class="active-content">10月迫啊死哦点击</div>
                <div class="active-date">2017-2-5</div>
            </div>
        </div>

        <my-footer/>
    </div>
</template>
l
<script>
    import MyFooter from '~/components/Footer.vue'
    import MyTop2 from '../components/top2'
    import encyAnd from '../components/encyand.vue'
    import Seach from '../components/seach.vue'
    import Pages from '../components/pages.vue'
    export default {
        name: "special",
        components:{
            MyFooter,MyTop2,encyAnd,Seach,Pages
        },
    }
</script>

<style scoped lang="less">
    .hot{
    overflow:auto; zoom:1;
    width: 1100px;
    margin: 80px auto 100px auto;
    .hot-title{
        font-size: 30px;
        color: #333;
        margin-bottom: 30px;
    }
    img{
        float: left;
        height: 420px;
        width: 555px;
        margin-right: 15px;
    }
    .images{
        width: 528px;
        float: right;
        .img-one{
            float: right;
            width: 253px;
            height: 200px;
            margin: 0 0 0 16px;
        }
        .img-two{
            float: right;
            width: 253px;
            height: 200px;
            margin: 0 0 0 0;
        }
        .img-three{
            float: right;
            width: 253px;
            height: 200px;
            margin: 18px 0 0 16px;
        }
        .img-four{
            float: right;
            width: 253px;
            height: 200px;
            margin: 18px 0 0 0;
        }
    }

}
    .active{
        width: 1100px;
        margin: 20px auto 30px auto;
        .active-title{
            height: 50px;
            line-height: 50px;
            border-bottom: 1px solid #ccc;
            padding-bottom: 5px;
            color: #333;
            .active-active{
                float: left;
                font-size: 22px;
            }
            .active-more{
                float: right;
            }
        }
        .line{
            width: 1100px;
            height: 10px;
        }
        .active-news{
            font-size: 14px;
            margin-top: 12px;
            height: 16px;
            .active-content{
                float: left;
            }
            .active-date{
                float: right;
            }
        }
    }
</style>