<template>
    <div class="pos">
        <div>
            <el-row>
                <el-col :span="7" class="pos-order" id="order-list">
                    点餐
                </el-col>

                <el-col :span="17">
                    商品展示
                </el-col>
            </el-row>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Pos",
        data() {
            return {}
        },
        mounted:function(){
            var orderHeight=document.body.clientHeight;
            document.getElementById("order-list").style.height=orderHeight+'px';
        }
    }
</script>

<style scoped>

</style>
