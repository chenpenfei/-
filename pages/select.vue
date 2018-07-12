<template>
    <!--<div class="ddl collapse driver cover-3">-->
        <!--<input id="ipt" type="text" placeholder="点击测试"/>-->
        <!--<ul id="ul">-->
            <!--<li>测试1</li>-->
            <!--<li>测试2</li>-->
            <!--<li>测试3</li>-->
            <!--<li>测试4</li>-->
            <!--<li>测试5</li>-->
            <!--<li>测试6</li>-->
        <!--</ul>-->
    <!--</div>-->
    <!--<div class="ddl collapse driver cover-3">-->
        <!--<input type="hidden" id="driverId" name="driverId" value="" />-->
        <!--<input type="text" placeholder="" readonly>-->
        <!--<ul>-->
            <!--<li data-value="001">张三</li>-->
            <!--<li data-value="111111">李四</li>-->
            <!--<li data-value="12345678910">哈哈</li>-->
            <!--<li data-value="你好">哇哈哈</li>-->
        <!--</ul>-->
    <!--</div>-->
</template>

<script>

export default {
        name: "select",
        data(){
            return{

            }
        },
        methods:{
            // select(){
            //     $(document).ready(function() {
            //         'use strict';
            //         var $driver = $('.driver'), $list = $driver.children('ul');
            //         $list.delegate('li', 'click', function() {
            //             var $this = $(this);
            //             document.getElementById("driverId").value = $this.attr('data-value');
            //             alert(document.getElementById("driverId").value);
            //         });
            //     });
            // }
//             select1(){
//                 var ipt=document.getElementById('ipt');
//                 var ul=document.getElementById('ul');
//                 var lis=ul.children;
//                 ipt.onfocus=function(){
//                     ul.style.display='block';
//                 }
//                 ipt.onblur=function(){
//                     setTimeout(function(){
//                         ul.style.display='none';
//                     },200)
//
//                 }
// //模拟option点击事件
//                 for(var i=0;i<lis.length;i++){
//                     lis[i].onclick=function(){
//                         ipt.value=this.innerText;
//                     }
//                 }
//             }
        }
    }
</script>

<style scoped>
    *{
        margin:0;
        padding:0;
        box-sizing:border-box;
    }
    #ul{
        margin-left:100px;
        list-style:none;
        width:150px;
        border:1px solid #000;
        display:none;
    }
    #ipt{
        margin:10px 0 0 100px;
    }
    li a{
        display:inline-block;
        width:100%;
        height:100%;
        text-decoration:none;
        color:#000;
    }
    li a:hover{
        background-color:blue;
    }
</style>