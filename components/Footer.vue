<template>
    <footer>
        <div class="foot1-big">
            <div class="foot1">
                <h1>友情链接</h1>
                <div class="link">
                    <a href="http://www.fooju.com.cn/">福居网资讯</a>
                    <a href="http://hhht.qu114.com/">呼和浩特去114</a>
                    <a href="http://bt.loupan.com/">包头房产网</a>
                    <a href="http://www.ttcy.com/">天堂草原音乐网</a>

                </div>
            </div>
        </div>

        <div class="foot2-big">
            <div class="foot2">
                <div class="top">
                    <a href="">关于我们</a>
                    <a href="">联系方式</a>
                    <a href="">隐私声明</a>
                    <a href="">版权声明</a>
                    <a href="">法律保障</a>
                </div>
                <div class="tips">温馨提示：呼和浩特房地产网最新购房信息请及时查看呼和浩特房地产业网官方网站【福居网】</div>
                <div class="address">地 址： 呼和浩特市赛罕区恩和大厦1909室 电 话:400-898-1018</div>
                <div class="website">北京福居网网络科技有限公司 Copyright © 2013-2017 FOOJU Corporation, All Rights Reserved 福居网 版权所有|
                    京ICP备13012924号-1
                </div>
                <div class="foot">
                    <img src="../assets/img/foot-1.png">
                    <img src="../assets/img/foot-2.gif">
                    <img src="../assets/img/foot-3.png">
                    <img src="../assets/img/foot-4.png">
                    <img src="../assets/img/foot-5.png">
                </div>
            </div>
        </div>

    </footer>
</template>

<style scoped lang="less">

    footer {
        width: 100%;
    }
    .foot1-big{
        background: #eeeeee;
        .foot1 {
            margin: 0 auto;
            height: 155px;
            width: 1200px;
            padding: 55px 0 0 120px;
            h1{
                font-size: 30px;
            }
            .link{
                margin: 20px 0 0 0;
                font-size: 14px;
                a{
                    color: #7f828b;
                    text-decoration: none;
                    margin: 0 40px 0 0;
                }
            }
        }
    }

    .foot2-big{
        .foot2 {
            text-align: center;
            color: white;
            height: 444px;
            background-image: url("../assets/img/footerBg.png");
            a {
                text-decoration: none;
                color: white;
            }
            .top {
                height: 18px;
                padding-top: 60px;
                margin-bottom: 30px;
            }
            .top a {
                margin: 0 55px;
            }
            .tips {
                height: 16px;
                margin-bottom: 30px;
                font-size: 14px;
            }
            .address {
                height: 16px;
                margin-bottom: 30px;
                font-size: 14px;
            }
            .website {
                height: 16px;
                margin-bottom: 70px;
                font-size: 14px;
            }
            .foot {
                height: 16px;
            }
            .foot img {
                margin: 0 2px;
            }
        }
    }


</style>