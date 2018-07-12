<template>
    <div>
        <my-top2/>
        <encyAnd/>

        <div class="content">
            <div class="title-top">
                <div id="sun">福居网> 二手房 >采光好</div>
                <div id="share">
                    <span>关注此房源</span>
                    <span>分享此房源</span>
                </div>
            </div>

            <div class="lighting">
                <h3>采光好</h3>

                <div class="vue-zoom-container"
                     v-scale="{options: currentOptions,url: minUrl}" ref="scaleBox">

                    <div class="vue-zoom-min-box _leftBox" >
                        <img src="../assets/img/pic1.png"  class="_minPic">
                        <div class="_vue-mask" @click="handleClick"></div>
                    </div>

                    <div class="vue-zoom-max-box _rightBox"  >
                        <img src="../assets/img/pic1.png"  class="_maxPic">
                    </div>

                    <div>
                        <div>45万</div>
                        <div>2室1厅</div>
                        <div>房源16</div>
                    </div>
                </div>
            </div>

            <div class="message"></div>
            <div class="feature"></div>
            <div class="picture"></div>
            <div class="assort"></div>
        </div>

        <my-footer/>
    </div>
</template>
l
<script>
    import MyFooter from '~/components/Footer.vue'
    import MyTop2 from '../components/top2'
    import encyAnd from '../components/encyandtwo.vue'
    export default {
        name: "secondDetails",
        components:{
            MyFooter,MyTop2,encyAnd
        },
        created:{
            getID(){
                let id = this.$route.params.id;
            }
        },
        props: {
            options: {
                type: Object
            },
            minUrl: {
                type: String
            }
        },
        data() {
            return {
                currentOptions: this.options,
                currentUrl: this.minUrl
            }
        },
        methods: {
            handleClick() {
                // console.log(this.minUrl)
            }
        },
        directives: {
            scale: {
                inserted(el,binding,vnode){
                    console.log(binding.value)
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
                console.log(this)
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
                float: right;
            }
        }
    }
    .lighting{
        h2{
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
        }
    }

</style>