//通用组件
<template>
    <div class="left-nav">
        <ul>
          <li>
            <i class="icon iconfont icon-wodezichan"></i>
            <div>收银</div>
          </li>
          <li>
            <i class="icon iconfont icon-jinrudianpu"></i>
            <div>店铺</div>
          </li>
          <li>
            <i class="icon iconfont icon-31quanbushangpin"></i>
            <div>商品</div>
          </li>
          <li>
            <i class="icon iconfont icon-31huiyuan"></i>
            <div>会员</div>
          </li>

        </ul>

    </div>
</template>

<script>
export default {
    name: 'leftNav',
    data() {
        return {

        }
    },
    mounted: function () {
        var orderHeight = document.body.clientHeight;
        document.getElementsByClassName("left-nav").style.height = orderHeight + 'px';
    }
}
</script>

<style>
.left-nav {
    color: #fff;
    font-size: 10px;
    width: 7%;
    height: 100%;
    background-color: #1D8ce0;
    float: left;
}

.iconfont {
    font-size: 24px;
}

.left-nav ul {
    padding: 0px;
    margin: 0px;
}

.left-nav li {
    list-style: none;
    text-align: center;
    border-bottom: 1px solid #20a0ff;
    padding:10px;
}

</style>
