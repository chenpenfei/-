<template>
    <div class="sidebar">
        <div class="sidebar-item">
            <a href="" target="_blank">
                <i class="iconfont icon-rili"></i>
                <p>日程</p>
            </a>
            <div class="sidebar-my">我的日程</div>
        </div>
        <div class="sidebar-item">
            <a href="" target="_blank">
                <i class="iconfont icon-shoucang1"></i>
                <p>关注</p>
            </a>
            <div class="sidebar-my">我的关注</div>
        </div>
        <div class="sidebar-item">
            <a href="" target="_blank">
                <i class="iconfont icon-fangzi"></i>
                <p>卖房</p>
            </a>
            <div class="sidebar-my">在线卖房</div>
        </div>
        <div class="sidebar-item">
            <a href="" target="_blank">
                <i class="iconfont icon-toolsbar"></i>
                <p>工具</p>
            </a>
            <div class="sidebar-my">房贷计算器</div>
        </div>
        <div class="sidebar-item">
            <a href="" target="_blank">
                <i class="iconfont icon-z-phone"></i>
                <p>APP</p>
            </a>
            <div class="pay">
                <img src="../assets/img/erweima.gif" style="width: 250px;height: 250px;">
            </div>
        </div>
    </div>
</template>

<style scoped lang="less">
    .sidebar{
        position: fixed;
        z-index: 998;
        right: 0;
        top: 20%;
        transform: translateY(-20%);
        text-align: center;
        background: #fff;
        height: 440px;
        width: 40px;
        .sidebar-item{
            position: relative;
            font-size: 14px;
            margin: 25px 0;
            padding: 5px 0;
            .pay{
                display: none;
                position: absolute;
                right: 50px;
                top: 50%;
                transform: translateY(-50%);
            }
            a{
                color: #000;
                .iconfont{
                    color: #000;
                    font-size: 26px;
                }
            }
            .sidebar-my{
                cursor: pointer;
                display: none;
                width: 70px;
                position: absolute;
                right: 50px;
                top: 50%;
                transform: translateY(-50%);
                padding: 10px 20px;
                text-overflow: ellipsis;
                white-space: nowrap;
                border-radius: 4px;
                background: #5f1985;
                color: #fff;
            }
            .sidebar-my::after{
                content: "";
                position: absolute;
                right: -16px;
                top: 50%;
                transform: translateY(-50%);
                border: 8px solid transparent;
                border-left: 8px solid #5f1985;
            }
            .sidebar-my .active{

            }
        }
        .sidebar-item .active{

        }
        .sidebar-item:hover{
            background: indigo;
            i{
                color: white;
            }
            p{
                color: white;
            }
            .sidebar-my{
                display: block;
            }
            .pay{
                display: block;
            }
        }
    }
</style>

<script>
    export default {
        name: "sidebar"
    }
</script>
