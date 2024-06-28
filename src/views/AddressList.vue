<!-- 地址页面 -->
<template>
    <div>
        <van-address-list
            v-model="chosenAddressId"
            :list="list"
            default-tag-text="默认"
            @add="onAdd"
            @edit="onEdit"
            @select="onselect"
        />
    </div>
</template>

<script>
import { Toast } from 'vant'
export default {
  data() {
    return {
      chosenAddressId: '1',
      list: [
        {
          id: '1',
          name: '张三',
          tel: '13000000000',
          address: '浙江省杭州市西湖区文三路 138 号东方通信大厦 7 楼 501 室',
          isDefault: true,
        },
        {
          id: '2',
          name: '李四',
          tel: '1310000000',
          address: '浙江省杭州市拱墅区莫干山路 50 号',
        },
      ]
    };
  },
  methods: {
    onAdd() {
      this.$router.push('/addressNew')
    },
    onEdit(item, index) {
      let data = JSON.stringify(item)
      this.$router.push({path:'/addressEdit',query:{item:data}})
    },
    onselect(item) {
      let instance = Toast('下单成功')
      setTimeout(() => {
        instance.close();
        this.$router.push('/detail')
      }, 1000);
    }
  },
}
</script>

<style>

</style>
