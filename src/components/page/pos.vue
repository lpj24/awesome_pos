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
                    </el-tab-pane>

                    <el-tab-pane label="挂单">
                        挂单
                    </el-tab-pane>

                    <el-tab-pane label="外卖">
                        外卖
                    </el-tab-pane>

                </el-tabs>


                <div class="order-btn">

                    <el-button type="warning">挂单</el-button>
                    <el-button type="danger">删除</el-button>
                    <el-button type="success"> 结账</el-button>

                </div>
            </el-col>

            <!--主界面右侧布局-->
            <el-col :span="16">
                <div class="often-goods">
                    <div class="often-title">常用商品</div>
                    <div class="often-goods-list">
                        <ul>
                            <li v-for="goods in oftenGoods">
                                <span>{{goods.goodsname}}</span>
                                <span class="o-price">￥{{goods.price}}</span>
                            </li>

                        </ul>
                    </div>
                </div>

                <!--商品分类-->
                <div class="goods-type">
                    <el-tabs>
                        <el-tab-pane label="汉堡">
                            <div class="often-goods-list">
                                <ul>
                                    <li v-for="goods in oftenGoods">
                                        <span>{{goods.goodsname}}</span>
                                        <span class="o-price">￥{{goods.price}}</span>
                                    </li>

                                </ul>
                            </div>
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
    export default {
        name: "Pos",
        data() {
            return {
                tableData: [
                    {goodsname: '鱼香寿司', count: 2, price: 16},
                    {goodsname: '红烧肉', count: 1, price: 45},
                    {goodsname: '水煮鱼', count: 1, price: 78},
                    {goodsname: '烤鱼', count: 1, price: 108},
                ],

                oftenGoods: [
                        {goodsname: '鱼香寿司', price: 16},
                        {goodsname: '红烧肉',  price: 45},
                        {goodsname: '水煮鱼',  price: 78},
                        {goodsname: '烤鱼', price: 108},
                        {goodsname: '海底捞', price: 108},
                        {goodsname: '宫爆鸡丁', price: 108},
                        {goodsname: '糖醋里脊', price: 108},
                        {goodsname: '串串', price: 108},
                ]
            }
        },
        mounted:function(){
            var orderHeight=document.body.clientHeight;
            document.getElementById("order-list").style.height=orderHeight+'px';
        },
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
</style>
