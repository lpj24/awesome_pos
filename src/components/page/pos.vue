<template>
    <div class='pos'>
        <el-row>
            <el-col :span='7' id="order-list" class="post-order">
                <el-tabs>
                    <el-tab-pane label="点餐">
                        <el-table :data="tableData" border style="width: 100%">
                            <el-table-column prop="goodsname" label="商品"></el-table-column>
                            <el-table-column prop="count" label="量"></el-table-column>
                            <el-table-column prop="price" label="金额"></el-table-column>

                            <el-table-column label="操作" fixed="right" width="100">
                                <template slot-scope="scope">
                                    <el-button type="text" size="small">删除</el-button>
                                    <el-button type="text" size="small">增加</el-button>
                                </template>
                            </el-table-column>
                        </el-table>

                        <div class="order-btn">

                            <el-button type="warning">挂单</el-button>
                            <el-button type="danger">删除</el-button>
                            <el-button type="success"> 结账</el-button>

                        </div>
                    </el-tab-pane>

                    <el-tab-pane label="挂单">
                        挂单
                    </el-tab-pane>

                    <el-tab-pane label="外卖">
                        外卖
                    </el-tab-pane>

                </el-tabs>

            </el-col>

            <!--主界面右侧布局-->
            <el-col :span="16">
                <div class="often-goods">
                    <div class="often-title">常用商品</div>
                    <div class="often-goods-list">
                        <ul>
                            <li v-for="goods in oftenGoods">
                                <span>{{goods.goodsName}}</span>
                                <span class="o-price">￥{{goods.price}}</span>
                            </li>

                        </ul>
                    </div>
                </div>

                <!--商品分类-->
                <div class="goods-type">
                    <el-tabs>
                        <el-tab-pane label="肉食">
                                <ul class="cookList">
                                    <li v-for="goods in meatGoods">
                                        <span class="foodImg">
                                            <img :src="goods.goodsImg" width="100%">
                                        </span>

                                        <span class="foodName">{{goods.goodsName}}</span>
                                        <span class="foodPrice">￥{{goods.price}}元</span>
                                    </li>

                                </ul>
                        </el-tab-pane>

                        <el-tab-pane label="小食">
                            挂单
                        </el-tab-pane>

                        <el-tab-pane label="饮料">
                            挂单
                        </el-tab-pane>

                        <el-tab-pane label="套餐">
                            外卖
                        </el-tab-pane>

                    </el-tabs>
                </div>
            </el-col>

        </el-row>
    </div>
</template>

<script>
    import axios from 'axios'
    export default {
        name: "Pos",
        created() {
            axios.get('http://jspang.com/DemoApi/oftenGoods.php').then(
                response=>{
                    console.log(response.data);
                    this.oftenGoods = response.data;
                }
            ).catch(error=>{
                alert('请求错误');
            })
        },
        data() {
            return {
                tableData: [
                    {goodsname: '鱼香寿司', count: 2, price: 16},
                    {goodsname: '红烧肉', count: 1, price: 45},
                    {goodsname: '水煮鱼', count: 1, price: 78},
                    {goodsname: '烤鱼', count: 1, price: 108},
                ],

                oftenGoods: [

                ],

                meatGoods: [
                    {goodsname: '鱼香寿司', price: 16, goodsImg: 'http://7xjyw1.com1.z0.glb.clouddn.com/pos001.jpg'},
                    {goodsname: '红烧肉',  price: 45, goodsImg: 'http://7xjyw1.com1.z0.glb.clouddn.com/pos001.jpg'},
                    {goodsname: '水煮鱼',  price: 78, goodsImg: 'http://7xjyw1.com1.z0.glb.clouddn.com/pos001.jpg'},
                    {goodsname: '烤鱼', price: 108, goodsImg: 'http://7xjyw1.com1.z0.glb.clouddn.com/pos001.jpg'},
                    {goodsname: '海底捞', price: 108, goodsImg: 'http://7xjyw1.com1.z0.glb.clouddn.com/pos001.jpg'},
                ]
            }
        }

    }
</script>

<style scoped>
    .pos {
        font-size: 12px;
    }

    .post-order {
        background-color: #F9FAFC;
        margin-left: 2px;
        border-right: 1px solid #C0CCDA;
    }

    .order-btn {
        margin-top: 10px;
        text-align: center;
    }

    .often-title {
        height: 20px;
        border-bottom: 1px solid #20a0ff;
        background-color: #F9FAFC;
        padding: 10px;
    }


    .often-goods-list ul li {
        list-style: none;
        float: left;
        padding: 10px;
        border-radius: 12px;
        margin: 7px;
        cursor: pointer;
        background-color: #ffffff;
    }
    .o-price {
        color: #20a0ff;
    }

    .goods-type {
        padding-left: 5px;
        clear: both;
    }

    .cookList li {
        list-style: none;
        width: 23%;
        float: left;
        padding: 2px;
        margin: 2px;
        border: 1px solid #E5E9F2;
        /*overflow: hidden;*/
        background-color: #fff;
        cursor: pointer;
    }

    .cookList li span {

        display: block;
        float: left;
    }

    .foodImg {
        width: 40%;
    }
</style>
