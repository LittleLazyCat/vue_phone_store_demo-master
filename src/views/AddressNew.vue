<!-- 修改地址页面 -->
<template>
    <div>
        <van-address-edit
            :area-list="areaList"
            show-delete
            @save="onSave"
            @delete="onDelete"
        />
    </div>
</template>

<script>
import AreaList from '../api/area'
import { Toast } from 'vant'
export default {
  name: "AddressNew",
  data() {
      return {
          areaList: AreaList
      }
  },
  methods: {
      onSave(item) {
          let instance = Toast('添加成功')
          setTimeout(() => {
            instance.close();
            this.$router.push('/addressList')
          }, 1000)
      },
      onDelete() {
        history.go(-1)
      }
  },
}
</script>

<style>

</style>
