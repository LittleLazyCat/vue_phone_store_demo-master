<!-- 订单信息 -->
<template>
    <div>
        <van-cell-group class="goods-cell-group">
            <van-cell>
                <van-col span="14" style="font-size: 13px">
                    <van-icon name="location-o" style="padding-right: 25px;" />
                    收货人：{{data.buyerName}}
                </van-col>
                <van-col style="font-size: 13px">电话号码:{{data.tel}}</van-col>
                <van-col span="21" style="padding-left: 43px;font-size: 13px">收货地址：{{data.address}}</van-col>
            </van-cell>
        </van-cell-group>

        <van-card
            :num="data.num"
            :price="data.price"
            :desc="data.specs"
            :title="data.phoneName"
            :thumb="data.icon"
        />

        <van-cell-group class="goods-cell-group">
            <van-cell class="goods-express">
                <van-col span="21">配送方式</van-col>
                <van-col>快递</van-col>
            </van-cell>
        </van-cell-group>

        <van-cell-group class="goods-cell-group">
            <van-cell class="goods-express" style="font-weight:bold">
                <van-col span="20">商品金额</van-col>
                <van-col style="color:red;">￥{{data.amount}}</van-col>
            </van-cell>
        </van-cell-group>

        <van-cell-group class="goods-cell-group">
            <van-cell class="goods-express" style="font-weight:bold">
                <van-col span="20">运费</van-col>
                <van-col style="color:red;">￥{{data.freight}}</van-col>
            </van-cell>
        </van-cell-group>
        <van-cell-group class="goods-cell-group">
            <van-cell class="goods-express" style="font-weight:bold">
                <van-col span="20">合计</van-col>
                <van-col style="color:red;">￥{{data.amount + data.freight}}</van-col>
            </van-cell>
        </van-cell-group>

        <van-cell-group class="goods-cell-group">
            <van-cell class="goods-express" style="font-weight:bold">
                <van-col span="20">订单状态</van-col>
                <van-col style="color:red;">{{payStatusTrans(data.payStatus)}}</van-col>
            </van-cell>
        </van-cell-group>
    </div>
</template>

<script>
export default {
  data() {
        return {
            data: {
                orderId: "1234567913245679",
                buyerName: "小明",
                phoneName: "Honor 8A",
                payStatus: 1,
                freight: 10,
                tel: "1363636363",
                address: "浙江省杭州市江干区780号",
                num: 1,
                specs: "32GB",
                price: "2800.00.00",
                icon: "https://img.yzcdn.cn/vant/apple-2.jpg",
                amount: 2800
            }
        }
    },
    methods: {
        payStatusTrans(status){
            if(status == 1) return '已支付'
            if(status == 0) return '未支付'
        }
    }
}
</script>

<style>

</style>
