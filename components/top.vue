<template>
    <header>
        <div class="content">
            <span @click="isLogin" style="cursor: pointer">请登录</span>
            <span type="gang">|</span>
            <a href="/regist">立即注册</a>
        </div>

        <div class="big">
            <div class="item">
                <span class="item1">
                    <a href="/">
                        <img src="../assets/img/logo.png">
                    </a>
                    <span class="item1-r" @click="click">呼和浩特
                        <img src="../assets/img/xia.png"></span>
                </span>
                <span class="item2">
                <a href="/" class="index" target="_blank">首页</a>
                <a href="/secondSchoolHomesList" target="_blank">二手房</a>
                <a href="/newHouseIndex" target="_blank">新房</a>
                <a href="/rentalList" target="_blank">租房</a>
                <a href="/schoolDistrictHousesList" target="_blank">学区房</a>
                <a href="/residentialQuartersList" target="_blank">小区</a>
                <a href="/brokerList" target="_blank">经纪人</a>
                <a href="/encyclopedias" target="_blank">百科</a>
                <a href="" target="_blank">
                    <el-dropdown class="line">
                      <span>在线委托</span>
                      <el-dropdown-menu slot="dropdown">
                        <el-dropdown-item>我是业主</el-dropdown-item>
                        <el-dropdown-item>帮我找房</el-dropdown-item>
                      </el-dropdown-menu>
                      </el-dropdown>
                </a>
                <a href="/tool">工具</a>
                <a href="/special">专题</a>
            </span>
            </div>
        </div>

        <div class="creat-content" v-if="Login">
            <div id="login-back">
                <i class="iconfont icon-cha" @click="closeLogin"></i>
            </div>

            <p class="creat-account">
                <span>登录</span>
                <a href="">没有账号，立即注册</a>
            </p>

            <form @submit.prevent>
                <div class="ipt">
                    <i class="iconfont icon-z-phone"></i>
                    <input type="tel" placeholder="请输入手机号"
                           id="phone" autocomplete="on" v-model="phone">
                </div>
                <div class="ipt">
                    <i class="iconfont icon-mima"></i>
                    <input type="password" placeholder="请输入密码"
                           id="password" v-model="pwd">
                </div>
                <button @click="login">登录</button>
            </form>

            <div class="click">
                <a href="">忘记密码?</a>
            </div>

            <div class="bottom">
                <a id="qq" class="fleft" target="_blank">
                    <img src="../assets/img/qq.jpg">
                    <br>
                    <span>qq登录</span>
                </a>
                <a id="weixin" class="fleft" target="_blank">
                    <img src="../assets/img/qq.jpg">
                    <br>
                    <span>微信登录</span>
                </a>
                <a id="weibo" class="fleft" target="_blank">
                    <img src="../assets/img/qq.jpg">
                    <br>
                    <span>微博登录</span>
                </a>
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
    </header>
</template>

<script>
    import md5 from '../node_modules/md5/md5'
    import axios from '../plugins/axios'
    import cookies from '../node_modules/js-cookie/src/js.cookie'
    export default {
        data(){
            return{
                show:"",
                Login : "",

                phone:17319052550,
                pwd:"zxc123123"
            }
        },
        methods: {
            click(){
                this.show = true
            },
            back(){
                this.show = false
            },
            isLogin(){
                this.Login = true
            },
            closeLogin(){
                this.Login = false
            },
            login(){
                let params = {
                    phone : this.phone,
                    password: md5(md5(this.pwd))+"fujuwang"
                };
                this.$axios.post("/api.php?s=Login/login",params).then(res=>{
                    console.log(params);
                    console.log(res);
                    if(res.data.code ==102){
                        alert("密码错误")
                    }else{

                    }

                })
            }
        }
    }
</script>

<style scoped lang="less">
    a {
        text-decoration: none;
    }
    .line{
        color: black;
        font-size: 15px;
    }
    .creat-content{
        /*opacity:.80;filter:alpha(opacity=80);*/
        text-align: center;
        background: white;
        position: fixed;
        left: 48%; top: 50%;
        transform: translate(-50%, -50%);

        z-index: 999;
        width: 620px;
        height: 476px;
        overflow: auto;
        #login-back{
            text-align: right;
            margin: 10px 20px;
           i{
               font-weight: inherit;
               font-size: 28px;
           }
        }
        .creat-account{
            width: 360px;
            margin: 0 auto 20px auto;
            height: 40px;
            line-height: 40px;
            span{
                float: left;
                font-size: 25px;
                color: #333;
            }
            a{
                float: right;
                font-size: 14px;
                color: #f90;
            }
        }
        form{
                clear: both;
            .ipt{
                margin: 20px auto;
                width: 360px;
                height: 50px;
                position: relative;
                i{
                    color: #aaa;
                    font-size: 18px;
                    position: absolute;
                    top: 17px;
                    left: 10px;
                }
                input{
                    padding-left: 32px;
                    margin: 0 auto;
                    width: 327px;
                    height: 50px;
                    border: 1px solid #ccc;
                    border-radius: 1px;
                }
            }
            button{
                width: 360px;
                background: #c30d23;
                color: #fff;
                text-align: center;
                height: 50px;
                line-height: 50px;
                border: none;
                margin-top: 20px;
            }
        }
        .click{
            margin-top: 30px;
            a{
                color: #aeaeae;
                font-size: 15px;
            }
            a:hover{
                color: #7f828b;
            }
        }
        .bottom{
            width: 360px;
            margin: 8px auto 0 auto;
            display: table;
            a{
                display: table-cell;
                img{
                    width: 50px;
                    height: 50px;
                    border-radius: 50%;
                    margin-bottom: 4px;
                }
                span{
                    font-size: 14px;
                    color: #555;
                }
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
    header {
        .content {
            width: 1100px;
            margin: 10px auto 0 auto;
            line-height: 23px;
            height: 23px;
            text-align: right;
            font-size: 12px;
            color: black;
            span[type]{
                margin: 0 10px;
            }
            a {
                color: black;
            }
        }
        .big{
            width: 100%;
            /*padding-bottom: 10px;*/
            .item {
                width: 1100px;
                margin: 0 auto;
                line-height: 70px;
                text-align: center;
                height: 70px;
                .item1{
                    float: left;
                    a {
                        img{
                            vertical-align: middle;
                        }
                    }
                    span {
                        padding: 6px;
                        margin: 0 0 0 25px;
                        border: 1px solid #777;
                        border-radius: 25px;
                        img {
                            margin: 0 0 -5px 0;
                        }
                    }
                }
                .item2 {
                    float: right;
                    font-size: 16px;
                    line-height: 70px;
                    a {
                        color: #333;
                        padding: 18px 0;
                        margin-left: 35px;
                }
                    a:hover {
                        color: red;
                        border-bottom: 2px solid red;
                    }
                    a.active{
                        color: red;
                        border-bottom: 2px solid red;
                    }
                }
            }
        }

    }
</style>











