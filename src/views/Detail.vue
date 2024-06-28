<!-- 订单详情页 -->
<template>
    <div class="goods">
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

        <van-submit-bar :price="data.amount*100 + data.freight*100" button-text="确认付款" @submit="onSubmit" />
    </div>
</template>

<script>
import {
    Tag,
    Col,
    Icon,
    Cell,
    Toast,
    CellGroup,
    Swipe,
    SwipeItem,
    GoodsAction,
    GoodsActionIcon,
    GoodsActionButton
    } from 'vant'

export default {
    components: {
        // [Tag.name]: Tag,
        // [Col.name]: Col,
        // [Icon.name]: Icon,
        // [Cell.name]: Cell,
        // [CellGroup.name]: CellGroup,
        // [Swipe.name]: Swipe,
        // [SwipeItem.name]: SwipeItem,
        // [GoodsAction.name]: GoodsAction,
        // [GoodsActionIcon.name]: GoodsActionIcon,
        // [GoodsActionButton.name]: GoodsActionButton
    },
    data() {
        return {
            data: {
                orderId: "1234567913245679",
                buyerName: "小明",
                phoneName: "Honor 8A",
                payStatus: 0,
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
        onSubmit:function () {
            let instance = Toast('支付成功');
            // setTimeout(() => {
            //     instance.close();
            //     this.$router.push('/success')
            // }, 1000);
            setTimeout(()=>{
                instance.close();
                this.$router.push('/success?orderId='+this.data.orderId+"$amount="+(this.data.amount+this.data.freight))
            },1000)
        }
    },
}
</script>

<style>

</style>
