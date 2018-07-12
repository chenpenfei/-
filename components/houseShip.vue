<template>
    <div class="all">
        <div class="top">
            <div class="tools-top">购房工具</div>
            <div class="tools-bottom">复杂的房贷税费计算，购房工具帮你解决</div>
        </div>

        <div class="middle">
            <div id="calculate1" @click="cal1">房贷计算器</div>
            <div id="calculate2">二手房税费计算器</div>
            <div id="calculate3">新房税费计算器</div>
        </div>

        <div class="bottom-content">
            <div id="bottom1" class="clearfix" >
                <form class="fleft" id="fangdai">
                    <div class="column">
                        <div class="column-left">贷款类型</div>
                        <div class="column-right">
                            <select name="loan_type" id="daikuaiType">
                                <option value="2">商业贷款</option>
                                <option value="1">公积金贷款</option>
                                <option value="3">组合贷款</option>
                            </select>
                        </div>
                    </div>
                    <div class="sy2gjj">
                        <div class="column">
                            <div class="column-left">计算方式</div>
                            <div class="column-right">
                                <select name="cal_mode" id="jisuanfangshi">
                                    <option value="1">面积、单价</option>
                                    <option value="2">贷款总额</option>
                                </select>
                            </div>
                        </div>
                        <div class="column danjia">
                            <div class="column-left">单价</div>
                            <div class="column-right">
                                <div class="inputGroup">
                                    <input type="text" placeholder="请输入大于0的数字" name="price" style="text-align:left">
                                    <span>元/平米</span>
                                </div>
                            </div>
                        </div>
                        <div class="column mianji">
                            <div class="column-left">面积</div>
                            <div class="column-right">
                                <input type="text" placeholder="请输入大于0的数字" name="area">
                            </div>
                            <div class="price" style="width: 34px">平米</div>
                        </div>
                        <div class="column anjiechengshu">
                            <div class="column-left">按揭成数</div>
                            <div class="column-right">
                                <select name="proportion" id="">
                                    <option value="0.9">9成</option>
                                    <option value="0.8">8成</option>
                                    <option value="0.7">7成</option>
                                    <option value="0.65">6.5成</option>
                                    <option value="0.6">6成</option>
                                    <option value="0.5">5成</option>
                                    <option value="0.4">4成</option>
                                    <option value="0.3">3成</option>
                                    <option value="0.2">2成</option>
                                </select>
                            </div>
                        </div>
                        <div class="column daikuanzonge">
                            <div class="column-left">贷款总额</div>
                            <div class="column-right">
                                <input type="text" placeholder="请输入大于0的数字" name="loan_total">
                            </div>
                            <div class="price" style="width: 22px">元</div>
                        </div>
                        <div class="column">
                            <div class="column-left">贷款期限</div>
                            <div class="column-right">
                                <select name="term" id="">
                                    <option value="360">30年（360期）</option>
                                    <option value="300">25年（300期）</option>
                                    <option value="240">20年（240期）</option>
                                    <option value="180">15年（180期）</option>
                                    <option value="120">10年（120期）</option>
                                    <option value="60">5年（60期）</option>
                                    <option value="12">1年（12期）</option>
                                </select>
                            </div>
                        </div>
                    </div>
                    <div class="zuhedai" style="display: none">
                        <div class="column">
                            <div class="column-left">商业性</div>
                            <div class="column-right">
                                <input type="text" placeholder="请输入大于0的数字" name="business_loan">
                            </div>
                            <div class="price" style="width: 22px">元</div>
                        </div>
                        <div class="column">
                            <div class="column-left">公积金</div>
                            <div class="column-right">
                                <input type="text" placeholder="请输入大于0的数字" name="public_loan">
                            </div>
                            <div class="price" style="width: 22px">元</div>
                        </div>
                        <div class="column">
                            <div class="column-left">贷款期限</div>
                            <div class="column-right">
                                <select name="" id="">
                                    <option value="">30年（360期）</option>
                                    <option value="">25年（300期）</option>
                                    <option value="">20年（240期）</option>
                                    <option value="">15年（180期）</option>
                                    <option value="">10年（120期）</option>
                                    <option value="">5年（60期）</option>
                                    <option value="">1年（12期）</option>
                                </select>
                            </div>
                        </div>
                        <div class="column">
                            <div class="column-left">公积金</div>
                            <div class="column-right">
                                <input type="text" value="3.25" name="publicTax">
                            </div>
                            <div class="price" style="width: 22px">%</div>
                        </div>
                    </div>
                    <div class="column dkll2sy">
                        <div class="column-left">贷款利率</div>
                        <div class="column-right">
                            <input type="text" value="4.9" class="daikuaililv" name="businessTax">
                        </div>
                        <div class="price" style="width: 22px">%</div>
                    </div>
                    <div class="column">
                        <div class="column-left">还款方式</div>
                        <div class="column-right">
                            <select name="repay_mode" class="huankuanfangshi">
                                <option value="1">等额本金</option>
                                <option value="2">等额本息</option>
                            </select>
                        </div>
                    </div>
                    <div class="submit" id="fdkaishi">开始计算</div>
                </form>

                <div class="result fright" id="result1">
                    <div class="text">计算结果</div>
                    <div class="Cal clearfix">
                        <span class="fleft">房款总额</span>
                        <span class="money fright">
                                <span class="number totalAmount">0</span>元</span>
                    </div>
                    <div class="Cal clearfix">
                        <span class="fleft">贷款总额</span>
                        <span class="money fright">
                                <span class="number loanTotal">0</span>元</span>
                    </div>
                    <div class="Cal clearfix">
                        <span class="fleft">还款总额</span>
                        <span class="money fright">
                                <span class="number repayTotal">0</span>元</span>
                    </div>
                    <div class="Cal clearfix">
                        <span class="fleft">支付利息款</span>
                        <span class="money fright">
                                <span class="number interestTotal">0</span>元</span>
                    </div>
                    <div class="Cal clearfix">
                        <span class="fleft">首期付款</span>
                        <span class="money fright">
                                <span class="number first">0</span>元</span>
                    </div>
                    <div class="Cal clearfix">
                        <span class="fleft">贷款月数</span>
                        <span class="money fright">
                                <span class="number loanMonths">0</span>（月）</span>
                    </div>
                    <div class="Cal clearfix">
                        <span class="fleft yuejunhuankuan">月均金额</span>
                        <span class="money fright">
                                <span class="number average">0</span>元
                                <span class="meiyuedijian">（每月递减
                                    <span>0</span>元）</span>
                            </span>
                    </div>
                </div>
            </div>
            <div id="bottom2" class="clearfix active" style="display: none">
                <form class="fleft" id="ershoufang">
                    <div class="column">
                        <div class="column-left">适用人群</div>
                        <div class="column-right">
                            <!--<select name="buy_status" id="">
                            <option value="1">买房</option>
                            <option value="2">卖房</option>
                        </select>-->
                            <input type="hidden" value="1" name="buy_status" readonly="readonly">
                            <input type="text" placeholder="买房" readonly="readonly">
                        </div>
                    </div>
                    <div class="column">
                        <div class="column-left">房屋类型</div>
                        <div class="column-right">
                            <select name="house_type" id="">
                                <option value="1">商品房</option>
                                <option value="2">房改房</option>
                            </select>
                        </div>
                    </div>
                    <div class="column">
                        <div class="column-left">卖方家庭唯一</div>
                        <div class="column-right">
                            <select name="is_only" id="">
                                <option value="1">唯一</option>
                                <option value="2">多套</option>
                            </select>
                        </div>
                    </div>
                    <div class="column">
                        <div class="column-left">距上次交易</div>
                        <div class="column-right">
                            <select name="age" id="">
                                <option value="1">未满两年</option>
                                <option value="2">满两年</option>
                                <option value="3">两年到五年</option>
                                <option value="4">满五年</option>
                            </select>
                        </div>
                    </div>
                    <div class="column">
                        <div class="column-left">买房家庭首套</div>
                        <div class="column-right">
                            <select name="is_first" id="">
                                <option value="1">首套</option>
                                <option value="2">两套</option>
                                <option value="3">三套以上</option>
                            </select>
                        </div>
                    </div>
                    <div class="column">
                        <div class="column-left">房屋面积</div>
                        <div class="column-right">
                            <input type="text" value="100" name="area">
                        </div>
                        <div class="price" style="width: 32px">平米</div>
                    </div>
                    <div class="column">
                        <div class="column-left">房屋单价</div>
                        <div class="column-right">
                            <input type="text" value="10000" name="price">
                        </div>
                        <div class="price" style="width: 52px">元/平米</div>
                    </div>
                    <div class="submit" id="esfkaishi">开始计算</div>
                </form>
                <div class="result fright" id="result2">
                    <div class="text">计算结果</div>
                    <div class="zonge clearfix">
                        <span class="fleft left">类型</span>
                        <span class="center fleft">税费详情</span>
                        <span class="money fright">费率占比</span>
                    </div>
                    <div class="zonge clearfix">
                        <span class="fleft left">税费合计</span>
                        <span class="center fleft">
                                <span class="number totalTax">0</span>
                            </span>
                        <span class="money fright">100%</span>
                    </div>
                    <div class="zonge clearfix">
                        <span class="fleft left">增值税</span>
                        <span class="center fleft">
                                <span class="number valAddTax">0</span>
                            </span>
                        <span class="money fright">0%</span>
                    </div>
                    <div class="zonge clearfix">
                        <span class="fleft left">契税</span>
                        <span class="center fleft">
                                <span class="number deedTax">0</span>
                            </span>
                        <span class="money fright">0%</span>
                    </div>
                    <div class="zonge clearfix">
                        <span class="fleft left">个税</span>
                        <span class="center fleft">
                                <span class="number peInTax">0</span>
                            </span>
                        <span class="money fright">0%</span>
                    </div>
                    <div class="zonge clearfix">
                        <span class="fleft left">土地出让金</span>
                        <span class="center fleft">
                                <span class="number laTransFees">0</span>
                            </span>
                        <span class="money fright">0%</span>
                    </div>
                </div>
            </div>
            <div id="bottom3" class="clearfix" style="display: none">
                <form class="fleft" id="xinfang">
                    <div class="column">
                        <div class="column-left">房屋面积</div>
                        <div class="column-right">
                            <input type="text" placeholder="100" name="area">
                        </div>
                        <div class="price" style="width: 32px">平米</div>
                    </div>
                    <div class="column">
                        <div class="column-left">房屋单价</div>
                        <div class="column-right">
                            <input type="text" placeholder="100" name="price">
                        </div>
                        <div class="price" style="width: 52px">元/平米</div>
                    </div>
                    <div class="column">
                        <div class="column-left">是否首套</div>
                        <div class="column-right">
                            <select name="number" id="">
                                <option value="1">首套</option>
                                <option value="2">两套</option>
                                <option value="3">三套以上</option>
                            </select>
                        </div>
                    </div>
                    <div class="submit" id="xfkaishi">开始计算</div>
                </form>
                <div class="result fright" id="result3">
                    <div class="text">计算结果</div>
                    <div class="zonge clearfix">
                        <span class="fleft">类型</span>
                        <span class="money fright">
                                <span class="number"></span>税费详情</span>
                    </div>
                    <div class="zonge clearfix">
                        <span class="fleft">契税</span>
                        <span class="money fright">
                                <span class="number deedTax">0</span>元</span>
                    </div>
                </div>
            </div>
        </div>




    </div>

</template>

<script>
    export default {
        name: "homeownership",
        data(){
            return{

            }
        },
        methods:{
            cal1(){
                let tab1 = el.querySelector('#calculate1');
                tab1.style.background = "#000";
                tab1.style.color = "#fff";
            }
        }
    }
</script>

<style scoped lang="less">
    button, select {
        text-transform: none;
    }
    .all{
        width: 1100px;
        margin: 0 auto;
        .top{
            margin: 20px auto 80px auto;
            width: 1100px;
            .tools-top{
                font-size: 40px;
                color: #333;
                margin-bottom: 10px;
                text-align: center;
            }
            .tools-bottom{
                font-size: 16px;
                color: #999;
                text-align: center;
            }
        }
        .middle{
            font-size: 16px;
            display: table;
            width: 400px;
            height: 40px;
            line-height: 40px;
            margin: 0 auto;
            border: 1px solid rgba(0,0,0,.1);
            text-align: center;
            #calculate1{
                cursor: pointer;
                display: table-cell;
                border: 1px solid #ccc;
            }
            .middle div:active{
                background: #000;
                color: #fff;
            }
            #calculate2{
                cursor: pointer;
                display: table-cell;
                border: 1px solid #ccc;
            }
            #calculate3{
                cursor: pointer;
                display: table-cell;
                border: 1px solid #ccc;
            }
        }
        .tool_content select {
            border: none;
            outline: 0;
            width: 100%;
            color: #666;
            appearance: none;
            padding-right: 14px;
        }

        .bottom-content{

            form{
                width: 480px;
                float: left;
                .column{
                    height: 50px;
                    line-height: 50px;
                    .column-left{
                        width: 110px;
                        float: left;
                    }
                    .column-right{
                        width: 370px;
                        float: left;
                        select,option{
                            border: none;
                        }
                        input{
                            outline: none;
                            border: none;
                        }
                    }
                }
            }
            .result{
                width: 480px;
                height: 427px;
                float: right;
                background: #ccc;
                .text{
                    font-size: 24px;
                    margin: 20px 0;
                }
                .cal {
                    font-size: 18px;
                    margin: 20px 0;
                }
            }
        }
    }

</style>