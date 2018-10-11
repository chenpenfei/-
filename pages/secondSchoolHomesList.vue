<template>
    <div>
        <my-top2/>
        <div class="SH-content" >
            <div class="SH-content-big">
                <div class="SH-content-title">
                    <img src="../assets/img/logo.png">
                    <a href="">在售</a>
                    <a href="">小区</a>
                    <a href="">地图找房</a>
                    <a href="">计算器</a>
                    <a href="">去估价</a>
                </div>
            </div>

            <div class="main" v-trans>
                <p>福居网> 二手房</p>

                <div class="SH-title-bottom">

                    <div>
                        <input type="text" placeholder="搜索">
                        <button>搜索</button>
                    </div>
                </div>

                <div class="top">
                    <!--区域-->
                    <div class="region">
                        <div class="region-tt">区域</div>
                        <div class="region-ct">
                            <el-checkbox @change="clearRegion"
                                         v-model="isChecked.r_id"
                                         style="float: left;margin: 0 30px 0 0;">
                                不限
                            </el-checkbox>
                            <el-checkbox-group v-model="formData.r_id"
                                               @change="RegionChange">
                                <el-checkbox v-for="(item,index) in fillData2.r_idData"
                                             :key="index" :label="item">
                                    {{item.title}}
                                </el-checkbox>
                            </el-checkbox-group>
                        </div>
                    </div>
                    <!--价格-->
                    <div class="price">
                        <div class="price-tt">价格</div>
                        <div class="price-ct">
                            <el-checkbox @change="clearPrice"
                                         v-model="Checked.checkPrice"
                                         style="float: left;margin: 0 30px 0 0;">
                                不限
                            </el-checkbox>
                            <el-checkbox-group v-model="formData.total_price"
                                               @change="PriceChange">
                                <el-checkbox v-for="price in fillData.total_priceData"
                                             :key="price.id" :label="price"
                                             style="float: left;margin: 0 30px  0 0;">
                                    {{price.title}}
                                </el-checkbox>
                            </el-checkbox-group>
                            <input type="text" style="width: 60px" v-model="formData.minPrice">
                            - <input type="text" style="width: 60px" v-model="formData.maxPrice"> 万
                            <button>确定</button>
                        </div>
                    </div>
                    <div class="house">
                        <div class="house-tt">户型</div>
                        <div class="house-ct">
                            <el-checkbox-group v-model="formData.bedroom">
                                <el-checkbox v-for="house in fillData.bedroomData" :label="house"
                                             :key="house.id"
                                             style="float: left;margin: 0 30px  0 0;">{{house.title}}</el-checkbox>
                            </el-checkbox-group>
                        </div>
                    </div>
                </div>

                <div class="middle">
                    <div class="flex-content" style="height: 0;" id="box" >
                        <slot>
                            <div class="house">
                                <div class="house-tt">类型</div>
                                <div class="house-ct">
                                    <el-checkbox-group v-model="formData.type">
                                        <el-checkbox v-for="genre in fillData.typeData"
                                            :label="genre" :key="genre.id"
                                                     style="float: left;margin: 0 30px  0 0;">{{genre.title}}</el-checkbox>
                                    </el-checkbox-group>
                                </div>
                            </div>
                            <div class="house">
                                <div class="house-tt">装修</div>
                                <div class="house-ct">
                                    <el-checkbox-group v-model="formData.decoration">
                                        <el-checkbox v-for="fitment in fillData.decorationData"
                                                     :label="fitment" :key="fitment.id"
                                                     style="float: left;margin: 0 30px  0 0;">{{fitment.title}}</el-checkbox>
                                    </el-checkbox-group>
                                </div>
                            </div>
                            <div class="dir">
                                <div class="dir-tt">朝向</div>
                                <div class="dir-ct">
                                    <el-checkbox-group v-model="formData.direction">
                                        <el-checkbox v-for="orientation in fillData.directionData"
                                                     :label="orientation" :key="orientation.id"
                                                     style="float: left;margin: 0 30px  0 0;">
                                            {{orientation.title}}
                                        </el-checkbox>
                                    </el-checkbox-group>
                                </div>
                            </div>

                            <!--面积-->
                            <div class="price">
                                <div class="price-tt">面积</div>
                                <div class="price-ct">
                                    <el-checkbox @change="clearArea"
                                                 v-model="Checked.checkArea"
                                                 style="float: left;margin: 0 30px 0 0;">
                                        不限
                                    </el-checkbox>
                                    <el-checkbox-group v-model="formData.built_area"
                                                       @change="AreaChange">
                                        <el-checkbox v-for="acreage in fillData.built_areaData"
                                                     :label="acreage" :key="acreage.id"
                                                     style="float: left;margin: 0 30px  0 0;">
                                            {{acreage.title}}
                                        </el-checkbox>
                                    </el-checkbox-group>
                                    <input type="text" style="width: 60px" v-model="formData.minCustom_bulit_area">
                                    - <input type="text" style="width: 60px" v-model="formData.maxCustom_bulit_area"> 万
                                    <button>确定</button>
                                </div>
                            </div>
                            <!--楼龄-->
                            <div class="house">
                                <div class="house-tt">楼龄</div>
                                <div class="house-ct">
                                    <el-checkbox @change="clearAge"
                                                 v-model="Checked.checkAge"
                                                 style="float: left;margin: 0 30px 0 0;">
                                        不限
                                    </el-checkbox>
                                    <el-checkbox-group v-model="formData.age"  @change="AgeChange">
                                        <el-checkbox v-for="age in fillData.ageData"
                                                     :label="age" :key="age.id"
                                                     style="float: left;margin: 0 30px  0 0;">
                                            {{age.title}}
                                        </el-checkbox>
                                    </el-checkbox-group>
                                </div>
                            </div>
                            <!--楼层-->
                            <div class="house">
                                <div class="house-tt">楼层</div>
                                <div class="house-ct">
                                    <el-checkbox @change="clearFloor"
                                                 v-model="Checked.checkFloor"
                                                 style="float: left;margin: 0 30px 0 0;">
                                        不限
                                    </el-checkbox>
                                    <el-checkbox-group v-model="formData.floor_type" @change="FloorChange">
                                        <el-checkbox v-for="floor in fillData.floor_typeData"
                                                     :label="floor" :key="floor.id"
                                                     style="float: left;margin: 0 30px  0 0;">
                                            {{floor.title}}
                                        </el-checkbox>
                                    </el-checkbox-group>
                                </div>
                            </div>
                            <div class="house">
                                <div class="house-tt">电梯</div>
                                <div class="house-ct">
                                    <el-checkbox-group v-model="formData.dianti">
                                    <el-checkbox v-for="elevator in fillData.diantiData"
                                                 :label="elevator" :key="elevator.id"
                                                 style="float: left;margin: 0 30px  0 0;">
                                        {{elevator.title}}
                                    </el-checkbox>
                                     </el-checkbox-group>
                                </div>
                            </div>

                            <div class="other">
                                <div class="other-tt">其他</div>
                                <div class="other-ct">
                                    <input type="text">
                                </div>
                                <button>确认</button>
                            </div>

                        </slot>
                    </div>
                </div>

                <div class="screen">
                    <slot>
                        <div class="screen-title">筛选分类</div>
                        <div class="screen-content">

                            <div class="screen-item" v-for="item in selectedData"
                            @click="deleteItem(item)">
                                {{item.title}}
                                <i class="iconfont icon-cha" ></i>
                            </div>

                            <div class="screen-clear" @click="clearAll">
                                <i class="iconfont icon-lajitong" ></i>
                                清除全部
                            </div>
                        </div>
                    </slot>
                </div>

                <div class="more-btn" style="cursor: pointer">
                    <span v-show="!isShow" @click="handleShow" id="btn1">更多选项 <i class="iconfont icon-jiantoushang" ></i></span>
                    <span v-show="isShow" @click="handleShow" id="btn2">收起选项 <i class="iconfont icon-jiantouxia" ></i></span>
                </div>

            </div>

            <div class="resource">

                <div class="rank">
                    <span v-for="(item,index) in fillData.orderData"
                          :class="{active: orderIndex == index}"
                            @click="changeActive(index)">
                        {{item.title}}
                        <input type="radio"  name="order" :value="item.id"
                               @change="getData" v-model="params.order">
                        <!--<i class="iconfont icon-jiantou1-copy-copy"></i>-->
                        <!--<i class="iconfont icon-jiantou1-copy-copy"></i>-->
                    </span>
                </div>

                <div class="region">
                    <div class="region-tt">筛选</div>
                    <div class="region-ct">
                        <el-checkbox class="region-ele">两年内</el-checkbox>
                        <el-checkbox class="region-ele">满两年</el-checkbox>
                        <el-checkbox class="region-ele">满五年</el-checkbox>
                        <el-checkbox class="region-ele">随时看房</el-checkbox>
                    </div>
                </div>

                <div class="find">
                    共找到
                    <span>{{findCount}}</span>
                    <span style="color: #000"> 呼和浩特
                        </span>房源
                </div>
                <div class="specific" v-for="(item,index) in clientArr" :key="index">
                    <nuxt-link :to="'/secondDetails?id='+item.id "
                               class="item-img fll">
                        <img :src="'http://www.fooju.cn'+item.pic">
                    </nuxt-link>
                    <div class="address">
                        <div id="address-test">{{item.title}}</div>
                        <p>
                            <span>{{item.village}}</span>
                            <span> | {{item.bedroom}}室{{item.livingroom}}厅{{item.wc}}卫</span>
                            <span> | {{item.direction}}</span>
                        </p>
                        <p>
                            <span>{{item.floor}}/{{item.livingroom}}</span>
                            <span> | {{item.decoration}}</span>
                        </p>
                        <p>
                            <span>{{item.age}}年建</span>
                            <span> | {{item.type}}</span>
                        </p>
                        <p>
                            <span>{{item.guanzhu_num}}人关注</span>
                            <span> | 共 {{item.daikan_num}}次带看</span>
                            <span> | 今天发布</span>
                        </p>
                    </div>
                    <div class="cost">
                        <div id="cost-money">
                            <span style="color: #c30d23;font-size: 40px">{{item.total_price}}</span>
                            <span style="color: #c30d23;font-size: 22px">万</span>
                        </div>
                        <div id="cost-meter">单价 {{item.unit_price}}元/平米</div>
                        <div id="cost-attention">关注</div>
                    </div>
                </div>

                <div class="page">
                    <el-pagination
                            background
                            layout="prev, pager, next"
                            :total="pageCount"
                            @current-change="handleNext">
                    </el-pagination>
                </div>
            </div>

        </div>
        <my-footer/>
    </div>
</template>
<script>
    import api from '~/mainApi/index'
    import axios from '~/plugins/axios'
    import MyFooter from '~/components/Footer.vue'
    import MyTop2 from '../components/top2'
    export default {
        name:"secondSchoolHomesList",
        components:{
            MyFooter,MyTop2
        },
        async asyncData() {
            let r_idData = await axios.get(api.paramToUrl(api.regionLists, {city: "呼和浩特"}))
            r_idData.data.data = r_idData.data.data.map(item => {
                item.title = item.area;
                return item
            })
            return {
                fillData2: {
                    r_idData: r_idData.data.data
                }
            }
        },
        data(){
            return{
                isShow:false,
                value: '',
                orderIndex:"0",
                Checked:{
                    checkRegion:"",
                    checkPrice:"",
                    checkArea:"",
                    checkAge:"",
                    checkFloor:"",
                },

                formData: {
                    r_id: [],
                    total_price: [],
                    bedroom: [],
                    minPrice: "",
                    maxPrice: "",
                    type: [],
                    decoration: [],
                    direction: [],
                    built_area: [],
                    minCustom_bulit_area: "",
                    maxCustom_bulit_area: "",
                    dianti: [],
                    age: [],
                    floor_type: [],
                    search: "",
                    order: 1
                },
                fillData: {
                    RegionData: [
                        {title: "金桥开发区", id: 0},
                        {title: "如意开发区", id: 1},
                        {title: "玉泉区", id: 2},
                        {title: "回民区", id: 3},
                        {title: "赛罕区", id: 4},
                        {title: "新城区", id: 5}],
                    total_priceData: [
                        {
                            title: "30万以下",
                            id: '0-30'
                        },
                        {
                            title: "30-40万",
                            id: '30-40'
                        },
                        {
                            title: "40-50万",
                            id: '40-50'
                        },
                        {
                            title: "50万以上",
                            id: '50-99999'
                        }
                    ],
                    bedroomData: [
                        {title: "一室", id: 0},
                        {title: "两室", id: 1},
                        {title: "三室", id: 2},
                        {title: "四室", id: 3},
                        {title: "五室", id: 4}
                    ],
                    typeData: [
                        {title: '平层', id: 0},
                        {title: '复式', id: 1},
                        {title: '跃层', id: 2}
                    ],
                    decorationData: [
                        {title: '毛坯', id: 0},
                        {title: '豪装', id: 1},
                        {title: '精装', id: 2},
                        {title: '简装', id: 3},
                        {title: '中装', id: 4}
                    ],
                    directionData: [
                        {title: '东', id: 0},
                        {title: '西', id: 1},
                        {title: '南', id: 2},
                        {title: '北', id: 3},
                        {title: '南北', id: 4},
                        {title: '西南', id: 5},
                        {title: '东北', id: 6},
                        {title: '东北', id: 7},
                        {title: '西北', id: 8},
                        {title: '东西', id: 9}
                    ],
                    built_areaData: [
                        {title: '50平以下', id: 1},
                        {title: '50-70平', id: 2},
                        {title: '70-90平', id: 3},
                        {title: '90以上', id: 4}
                    ],
                    diantiData: [{id: 0, title: '是'}, {id: 1, title: '否'}],
                    ageData: [
                        {id: 1, title: '5年以内'},
                        {id: 2, title: '10年以内'},
                        {id: 3, title: '15年以内'},
                        {id: 4, title: '15年以上'}
                    ],
                    floor_typeData: [
                        {id: 1, title: "底层"},
                        {id: 2, title: "低楼层"},
                        {id: 3, title: "中层"},
                        {id: 4, title: "中高层"},
                    ],
                    orderData: [
                        {
                            title: "最新",
                            id: 1
                        },
                        {
                            title: "房屋总价",
                            id: 2
                        },
                        {
                            title: "房屋单价",
                            id: 6
                        },
                        {
                            title: "房屋面积",
                            id: 4
                        }
                    ]
                },
                isChecked: {
                    r_id: true,
                    total_price: true,
                    built_area: true,
                    floor_type: true
                },
                orderComputed: {},
                params: {
                    page_size: 10,
                    page_num: 1,
                    order: 1,
                },

                clientArr:[],
                findCount:"",
                clientData:{
                    add_time: "",
                    address: "",
                    age: "",
                    bedroom: "",
                    built_area: "",
                    daikan_num: "",
                    decoration: "",
                    dianti: "",
                    direction: "",
                    fabushijian: "",
                    floor: "",
                    floor_totle: "",
                    guanzhu_num: "",
                    guapai: "",
                    htype: "",
                    id: "",
                    livingroom: "",
                    number: "",
                    pic: "",
                    property_right: "",
                    title: "",
                    total_price: "",
                    type: "",
                    unit_price: "",
                    v_id: "",
                    village: "",
                    wc: "",
                },
                pageCount:0
            }
        },
        computed: {
            selectedData() {
                let formData = this.formData;
                let allData = [];
                for (let key in formData) {
                    if (formData[key] instanceof Array) {
                        formData[key].map(item => {
                            item._parentName = key;
                        })
                        allData.push(...formData[key]);
                    }
                }
                return allData;
            },
        },
        watch:{
            selectedData() {
                this.getData();
            }
        },
        mounted() {
            this.getData();
        },
        methods: {
            msg(){
              let item = el.querySelector(".")
            },
            handleShow(isShow){
                this.isShow = !this.isShow;
            },
            changeActive(index){
                this.orderIndex = index;
                console.log(this.params.order);
            },
            clearRegion(){
                this.formData.r_id=[];
            },
            RegionChange(){
                this.isChecked.r_id = false
            },
            clearPrice(){
                this.formData.total_price=[];
            },
            PriceChange(){
                this.Checked.checkPrice = false
            },
            clearArea(){
                this.formData.built_area=[];
            },
            AreaChange(){
                this.Checked.checkArea = false
            },
            clearAge(){
                this.formData.age=[];
            },
            AgeChange(){
                this.Checked.checkAge = false
            },
            clearFloor(){
                this.formData.floor_type=[];
            },
            FloorChange(){
                this.Checked.checkFloor = false
            },

            handleClear(key) {
                if (this.isChecked[key]) {
                    this.formData[key].splice(0);
                }
            },
            getData() {

                let formData = this.formData;
                let params = {...this.params};
                for (let key in formData) {
                    if (formData[key] instanceof Array&&formData[key].length>0) {
                        params[key] = formData[key].map(item => item.id)
                    }
                }
                if(this.userid){
                    params.userid = this.userid
                }
                const loading = this.$loading({
                    lock: true,
                    text: '数据加载中...',
                    spinner: 'el-icon-loading',
                    background: 'rgba(0, 0, 0, 0.7)'
                });
                axios.get(api.paramToUrl("api.php?s=Product/used_lists", params)).then(res => {
                    this.clientArr = res.data.data;
                    this.findCount = res.data.count;
                    this.pageCount = res.data.count;
                    console.log(this.clientArr);
                    // console.log(res.data);

                    loading.close()
                }).catch(err => {
                    loading.close()
                })
            },
            deleteItem(item){
                let index = this.formData[item._parentName].findIndex(val => val == item.id);
                this.formData[item._parentName].splice(index, 1)
            },
            handleChange(val) {
                if (this.formData[val].length > 0) {
                    this.isChecked[val] = false;
                }
                else {
                    this.isChecked[val] = true;
                }
            },
            clearAll(){
                let formData = this.formData;
                for (let arr in formData) {
                    if (formData[arr] instanceof Array) {
                        formData[arr].splice(0);
                        this.handleChange(arr);
                    }
                }
            },
            handleNext(val) {
                console.log(val)
                this.params.page_num = val;
                this.getData();
            }
        },
        directives:{
            trans:{
                inserted(el,biding,vnode){
                    let box = el.querySelector('#box');
                    let btn1 = el.querySelector('#btn1');
                    let btn2 = el.querySelector('#btn2');
                    btn1.onclick= function(){
                        box.style.height = "auto";
                        let targetHeight = getComputedStyle(box).height;
                        box.style.height = 0;
                        box.offsetHeight;
                        box.style.height = targetHeight;
                    }
                    btn2.onclick = function(){
                        box.style.height = 0;
                    }

                }
            }
        }
    }
</script>
<style>
    .el-checkbox__input.is-checked .el-checkbox__inner,
    .el-checkbox__input.is-indeterminate .el-checkbox__inner {
        background: #c30d23;
        border-color: #c30d23;
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
        .SH-content-big{
            width: 100%;
            border-bottom: 1px solid #ccc;
            .SH-content-title{
                height: 80px;
                line-height: 80px;
                width: 1100px;
                margin: 0 auto;
                background: white;
                img{
                    vertical-align: middle;
                    margin-right: 20px;
                }
                a{
                    font-size: 16px;
                    color: black;
                    margin: 0 0 0 55px;
                }
                a:hover{
                    color: red;
                }
            }
        }
        .main{
            width: 1100px;
            margin: 0 auto;
            p{
                height: 70px;
                line-height: 60px;
                color: #7f828b;
                font-size: 14px;
            }
            .SH-title-bottom{
                height: 70px;
                width: 1100px;
                margin: 0 auto;
                line-height: 70px;
                color: #7f828b;
                font-size: 14px;
                input{
                    outline:none;
                    font-size: 15px;
                    padding: 0 0 0 20px;
                    background: #eee;
                    border: none;
                    height: 60px;
                    width: 720px;
                }
                button{
                    height: 60px;
                    width: 160px;
                    background: #c30d23;
                    border: none;
                    font-size: 16px;
                    color: white;
                }
            }
            .top{
                width: 1100px;
                margin: 0 auto;
                .region{
                    height: 78px;
                    margin: 25px 0 10px 0;
                    .region-tt {
                        float: left;
                        width: 100px;
                        font-size: 14px;
                        padding: 8px 0;
                    }
                    .region-ct {
                        line-height: 38px;
                        float: left;
                        height: 78px;
                        width: 560px;
                        el-checkbox-group{
                            float: left;
                        }
                    }
                }
                .price{
                    height: 78px;
                    margin: 25px 0 10px 0;
                    .price-tt {
                        float: left;
                        width: 100px;
                        font-size: 14px;
                        padding: 8px 0;
                    }
                    .price-ct{
                        line-height: 38px;
                        float: left;
                        height: 78px;
                        width: 560px;
                        button{
                            width: 50px;
                            height: 26px;
                            background: #c30d23;
                            border: none;
                            color: #fff;
                            font-size: 14px;
                            margin-left: 10px
                             }
                        }
                    }
                .house{
                    height: 39px;
                    margin: 25px 0 10px 0;
                    .house-tt {
                        float: left;
                        width: 100px;
                        font-size: 14px;
                        padding: 8px 0;
                    }
                    .house-ct {
                        line-height: 38px;
                        float: left;
                        height: 39px;
                        width: 560px;
                    }
                }
                 }
            .middle{

                width: 1100px;
                margin: 0 auto;
                .flex-content{
                    padding-right: 350px;
                    transition: height ease .5s;
                    overflow: hidden;
                    .house{
                        width: 650px;
                        height: auto;
                        margin: 25px 0 10px 0;
                        .house-tt {
                            float: left;
                            width: 100px;
                            height: 39px;
                            font-size: 14px;
                            padding: 8px 0;
                        }
                        .house-ct {
                            line-height: 38px;
                            height: 39px;
                            width: 660px;
                        }
                    }
                    .dir{
                        width: 650px;
                        height: auto;
                        margin: 25px 0 10px 0;
                        .dir-tt {
                            float: left;
                            width: 100px;
                            height: 39px;
                            font-size: 14px;
                            padding: 8px 0;
                        }
                        .dir-ct {
                            line-height: 38px;
                            height: 39px;
                            width: 760px;
                        }
                    }
                    .price{
                        clear: both;
                        height: 78px;
                        margin: 25px 0 10px 0;
                        .price-tt {
                            float: left;
                            width: 100px;
                            height: 39px;
                            font-size: 14px;
                            padding: 8px 0;
                        }
                        .price-ct{
                            line-height: 38px;
                            float: left;
                            height: 78px;
                            width: 560px;
                            button{
                                width: 50px;
                                height: 26px;
                                background: #c30d23;
                                border: none;
                                color: #fff;
                                font-size: 14px;
                                margin-left: 10px
                            }
                        }
                    }
                    .other{
                        clear: both;
                        height: 38px;
                        line-height: 38px;
                        margin: 25px 0 10px 0;
                        .other-tt {
                            float: left;
                            width: 100px;
                            height: 22px;
                            line-height: 22px;
                            font-size: 14px;
                            padding: 8px 0;
                        }
                        .other-ct{
                            line-height: 38px;
                            float: left;
                            height: 38px;
                            width: 200px;
                        }
                        button{
                            width: 50px;
                            height: 26px;
                            background: #c30d23;
                            border: none;
                            color: #fff;
                            font-size: 14px;
                            margin-left: 10px
                        }
                    }
                }
            }
            .screen {
                overflow: auto;
                width: 1100px;
                height: auto;
                margin: 10px auto;
                .screen-title {
                    float: left;
                    width: 100px;
                    font-size: 14px;
                    padding: 8px 0;
                    margin: 10px 0;
                }
                .screen-content{
                    line-height: 48px;
                    margin: 10px 0;
                    width: 700px;
                    float: left;
                    .screen-item{
                        float: left;
                        height: 26px;
                        line-height: 26px;
                        width: 110px;
                        color: #c30d23;
                        font-size: 14px;
                        border: 1px solid #ccc;
                        text-align: center;

                        margin-right: 20px;
                        margin-bottom: 20px;
                        .iconfont{
                            float: right;
                            background: #ccc;
                            padding: 0 4px;
                            color: #ffffff;
                        }
                    }
                    .screen-clear {
                        cursor: pointer;
                        line-height: 26px;
                        height: 26px;
                        margin-left: 10px;
                        float: left;
                        width: 100px;
                        font-size: 14px;
                        padding: 0 0 8px 0;
                        .iconfont {
                            font-size: 20px;
                        }
                    }
                }

            }
            .more-btn{
                clear: both;
                text-align: center;
                font-size: 16px;
                color: #7f828b;
                width: 1100px;
                padding: 25px 0;
                margin: 20px auto;
                border-bottom: 1px solid #ccc;
            }
        }
        .resource{
            width: 1100px;
            margin: 100px auto 0 auto;
            .rank{
                cursor: pointer;
                height: 42px;
                span{
                    margin-right: 20px;
                    font-size: 18px;
                    border: 1px solid #c30d23;
                    color: #c30d23;
                    /*color: #fff;*/
                    /*background: #c30d23;*/
                    padding: 10px 20px;
                    border-radius: 20px;
                    /*input{*/
                        /*display: none;*/
                    /*}*/
                }
                span:hover{
                    color: #fff;
                    background: #c30d23;
                }
            }
            .rank span.active{
                    background: #c30d23;
                    color: #fff;
            }
            .region{
                height: 39px;
                margin: 10px 0 10px 0;
                .region-tt {
                    color: #222;
                    float: left;
                    width: 100px;
                    font-size: 14px;
                    padding: 8px 0;
                }
                .region-ct {
                    line-height: 38px;
                    float: left;
                    height: 39px;
                    width: 560px;
                    .region-ele{
                        color: #888;
                        margin: 0 28px 0 0 ;
                    }
                }
            }
            .find{
                margin: 20px 0 20px 0;
                color: #222;
                font-size: 30px;
                span{
                    color: red;
                }
            }
            .specific{
                margin-top: 40px;
                height: 217px;
                img{
                    float: left;
                    height: 214px;
                    width: 285px;
                }
                .address{
                    float: left;
                    width: 605px;
                    height: 214px;
                    padding: 0 30px;
                    #address-test{
                        color: #333;
                        font-size: 20px;
                        margin-bottom: 30px;
                    }
                    p{
                        margin: 17px 0;
                    }
                }
                .cost{
                    float: left;
                    width: 150px;
                    height: 214px;
                    text-align: right;
                    #cost-money{
                        margin-bottom: 10px
                    }
                    #cost-meter{
                        margin: 20px 0;
                        color: #555;
                        font-size: 14px;
                    }
                    #cost-attention{
                        cursor: pointer;
                        color: #c30d23 ;
                        float: right;
                        text-align: center;
                        font-size: 16px;
                        margin: 20px 0;
                        padding: 10px 0;
                        width: 100px;
                        border: 1px solid #c30d23;
                        border-radius: 5px;
                    }
                }
            }
            .page{
                text-align: right;
                height: 105px;
                margin: 50px 0 40px 0 ;
                el-pagination{
                    background: #5f1985;
                }
            }
        }

    }

</style>