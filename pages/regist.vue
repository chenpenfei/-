<template>
    <div class="creat">
        <header class="dtop">
            <a href="/" class="dtop-left"><img src="../assets/img/logo.png"></a>
            <a href="/" target="_blank" class="dtop-right">
                <span>返回福居网首页</span>
                <img src="../assets/img/return.png">
            </a>
        </header>

        <div class="creat-content">
            <p class="creat-account">
                <span>创建账号</span>
                <a href="">已有账号，立即登录</a>
            </p>

            <div class="one">
                <i class="iconfont icon-z-phone"></i>
                <input class="one-btn1" type="text"
                       placeholder="请输入手机号" v-model="registerData.phone"
                       @keyup="inputPhone">
            </div>

            <div class="phoneErrorMsg">111</div>

            <div class="two">
                <i class="iconfont icon-mima"></i>
                <input type="text" placeholder="请输入短信验证码"
                       class="two-btn2" v-model="registerData.note">
                <button class="get">获取验证码</button>
            </div>

            <div class="three">
                <i class="iconfont icon-mima"></i>
                <input type="password" placeholder="请输入6-18为密码"
                       class="three-btn3" v-model="registerData.password">
            </div>

            <div class="passErrorMsg">密码格式不正确！</div>

            <div class="four">
                <i class="iconfont icon-nicheng"></i>
                <input type="text"   placeholder="请输入昵称"
                       class="four-btn4"  v-model="registerData.nickname">
            </div>

            <div class="nameErrorMsg">昵称格式不正确！</div>

            <div class="regist-btn">
                <button type="button" @click="submit">立即注册</button>
            </div>

            <div class="click">
                <span>点击立即注册，则表示您阅读并同意遵守</span>
                <a href=""> 福居网平台服务协议</a>
            </div>
        </div>

        <footer>
            <p>北京福居网网络科技有限公司|
                Copyright © 2013-2017 FOOJU Corporation,
                All Rights Reserved 福居网 版权所有| 京ICP备13012924号-1</p>
        </footer>
    </div>
</template>

<script>
    import api from '~/mainApi/index'
    import axios from '~/plugins/axios'
    export default {
        name: "register",
        data(){
          return{
              registerData:{
                  phone:"",
                  note:"",
                  password:"",
                  nickname:"",
                  msg:""
              },
              phoneErrorMsg:"",
              passErrorMsg:"",
              nameErrorMsg:""
          }
        },
        created(){

        },
        methods:{
            inputPhone(){
                    let mobileReg = /((13[0-9])|(14[5,7])|(15[0-3,5-9])|(17[0,3,5-8])|(18[0-9])|166|198|199|(147))\d{8}$/
                    this.phoneErrorMsg = mobileReg.test(this.registerData.phone) ? ""
                        : "请输入正确的手机号码";
                        this.phoneErrorMsg = true
            },
            submit() {
                axios.get(`/api.php?s=Msg/verify/mobile/${this.registerData.phone}/verify/
            ${this.registerData.phone}`).then(res => {
                    console.log(res.code)
                    if (res.data.code != 200) {
                        this.phoneErrorMsg = res.data.msg;
                    } else {
                        let params = {
                            password: md5(md5(this.registerData.password)) + "fujuwang",
                            mobile: this.registerData.phone,
                            name: this.registerData.nickname
                        }
                        axios.post("/api.php?s=Login/register", params).then(res => {
                            console.log(res)
                        }).catch(err => {
                        })
                    }
                }).catch(err => {
                    console.log(err)
                })
            }
        }
    }
</script>

<style scoped lang="less">
    *{
        padding: 0;
        margin: 0;
    }
    .phoneErrorMsg,.passErrorMsg,.nameErrorMsg,.nameErrorMsg{

        color: red;
        width: 360px;
        margin: 10px auto;
        text-align: left;
    }
.creat{
    background: #dbe1ec;
    text-align: center;
    .dtop{
        background: white;
        height: 80px;
        text-align: left;
        .dtop-left{
            img{
                margin: 20px 0 0px 120px;
            }
        }
        .dtop-right{
            color: #555;
            height: 40px;
            position: relative;
            top: -15px;
            left: 840px;
            span{
                font-size: 13px;
                margin: 5px;
            }
            img{
                vertical-align: middle;
            }
        }
    }
    .creat-content{
        width: 360px;
        padding: 40px 130px;
        margin: 30px auto;
        background: #fff;

        .creat-account{
            text-align: left;
            width: 360px;
            margin: 15px auto 15px auto;
            span{
                margin-right: 100px;
                font-weight: bold;
                font-size: 30px;
            }
            a{
                font-size: 14px;
                color: orange;
                text-decoration: none;
            }
        }
        .one{
            position: relative;
            width: 360px;
            margin: 0 auto;
            i{
                color: #aaa;
                font-size: 18px;
                position: absolute;
                top: 26px;
                left: 10px;
            }
            .one-btn1{
                padding-left: 32px;
                margin: 10px auto;
                width: 320px;
                height: 50px;
            }
        }
        .two{
            position: relative;
            width: 360px;
            margin: 10px auto;
            i{
                color: #aaa;
                font-size: 18px;
                position: absolute;
                top: 23px;
                left: 10px;
            }
            .two-btn2{
                padding-left: 32px;
                width: 198px;
                height: 52px;
                margin-right: 10px;
            }
            .get{
                outline: none;
                color: #777;
                width: 110px;
                height: 54px;
                border: 1px solid #999;
                background: 0 0;
            }
        }
        .three{
            position: relative;
            width: 360px;
            margin: 0 auto;
            i{
                color: #aaa;
                font-size: 18px;
                position: absolute;
                top: 26px;
                left: 10px;
            }
            .three-btn3{
                padding-left: 32px;
                margin: 10px auto;
                width: 320px;
                height: 50px;
            }
        }
        .four{
            position: relative;
            width: 360px;
            margin: 0 auto;
            i{
                color: #aaa;
                font-size: 18px;
                position: absolute;
                top: 26px;
                left: 10px;
            }
            .four-btn4{
                padding-left: 32px;
                margin: 10px auto;
                width: 320px;
                height: 50px;
            }
        }

        .creat-btn{
                margin: 10px 0;
                width: 350px;
                height: 50px;
            }
        button[type]{
            width: 356px;
            height: 50px;
            background: firebrick;
            border: none;
            color: white;
            font-size: 16px;
            margin-top: 10px;
        }
        .click{
            color: #7f828b;
            font-size: 13px;
            margin-top: 20px;
            a{
                font-weight: bold;
                color: black;
                text-decoration: none;
            }
        }
    }
    footer{
        height: 80px;
        background: #dbe1ec;
        line-height: 80px;
        font-size: 14px;
        color: #777;
        text-align: center;
        position: absolute;
        bottom: -90px;
        right: 0;
        left: 0;
    }
}
</style>




