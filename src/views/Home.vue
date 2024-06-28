<template>
  <div class="home">
    <!-- Tab 标签页的标签 -->
    <van-tabs @click="onClick" sticky title-active-color="#6cfe" color="#6cfe" :line-width="100" :line-height="2">
      <van-tab v-for="index in categories.length" :key="index" :title="categories[index-1].name" class="tab">
        <!-- 循环每一页的内容 -->
        <van-card v-for="(item, index) in phones" :key="index"
          :price="item.price"
          :desc="item.desc"
          :title="item.title"
          :thumb="item.thumb"
        >
          <template #tags>
            <van-tag v-for="(tag, index) in item.tag" :key="index" color="#f2826a" style="margin-left: 5px;">{{tag.name}}</van-tag>
          </template>
          <template #footer>
            <van-button round color="linear-gradient(to right, #56CCF2, #2F80ED)" size="mini" @click="buy(index)">购买</van-button>
          </template>
        </van-card>

      </van-tab>
    </van-tabs>
    <!-- Sku 商品规格 -->
    <van-sku
      v-model="show"
      :sku="sku"
      :goods="goods"
      :hide-stock="sku.hide_stock"
      @buy-clicked="onBuyClicked"
    />
  </div>
</template>

<script>

export default {
  name: 'Home',
  components: {
  },
  data() {
    return {
      categories: [
        {
          name: '魅焰红',
          type: 1
        },
        {
          name: '极光蓝',
          type: 2
        },
        {
          name: '铂光金',
          type: 3
        },
        {
          name: '幻夜黑',
          type: 4
        }
      ],
      // 第一页的内容
      phones: [
        {
          id: 1,
          title: "Honor 8A",
          price: "2800.00",
          desc: "魅焰红",
          tag: [
            {
              name: "720P珍珠屏"
            },
            {
              name: "Micro USB接口"
            }
          ],
          thumb: "https://img.yzcdn.cn/vant/ipad.jpeg"
        },{
          id: 8,
          title: "FDFDG 8A",
          price: "7894.00",
          desc: "魅焰红",
          tag: [
            {
              name: "720P珍珠屏"
            },
            {
              name: "Micro USB接口"
            }
          ],
          thumb: "https://img.yzcdn.cn/vant/ipad.jpeg"
        },{
          id: 5,
          title: "CBCB 8A",
          price: "3434.00",
          desc: "魅焰红",
          tag: [
            {
              name: "720P珍珠屏"
            },
            {
              name: "Micro USB接口"
            }
          ],
          thumb: "https://img.yzcdn.cn/vant/ipad.jpeg"
        }
      ],
      show: true,
      sku: '',
      goods: ''
    }
  },
  created () {
  },
  methods: {
    onClick(index) {
      // Tab 标签页的内容
      switch (index) {
        case 0:
          this.phones = [
            {
              id: 1,
              title: "Honor 8A",
              price: "2800.00",
              desc: "魅焰红",
              tag: [
                {
                  name: "720P珍珠屏"
                },
                {
                  name: "Micro USB接口"
                }
              ],
              thumb: "https://img.yzcdn.cn/vant/ipad.jpeg"
            },{
              id: 8,
              title: "FDFDG 8A",
              price: "7894.00",
              desc: "魅焰红",
              tag: [
                {
                  name: "720P珍珠屏"
                },
                {
                  name: "Micro USB接口"
                }
              ],
              thumb: "https://img.yzcdn.cn/vant/ipad.jpeg"
            },{
              id: 5,
              title: "CBCB 8A",
              price: "3434.00",
              desc: "魅焰红",
              tag: [
                {
                  name: "720P珍珠屏"
                },
                {
                  name: "Micro USB接口"
                }
              ],
              thumb: "https://img.yzcdn.cn/vant/ipad.jpeg"
            }
          ]
          break;
        case 1:
          this.phones = [
            {
              id: 2,
              title: "CBCB 8A",
              price: "3434.00",
              desc: "极光蓝",
              tag: [
                {
                  name: "720P珍珠屏"
                },
                {
                  name: "Micro USB接口"
                }
              ],
              thumb: "https://img.yzcdn.cn/vant/ipad.jpeg"
            }
          ]
        break;
        case 2:
          this.phones = [
            {
              id: 3,
              title: "FGFGFH 8A",
              price: "4564.00",
              desc: "铂光金",
              tag: [
                {
                  name: "720P珍珠屏"
                },
                {
                  name: "Micro USB接口"
                }
              ],
              thumb: "https://img.yzcdn.cn/vant/ipad.jpeg"
            }
          ]
        break;
        case 3:
          this.phones = [
            {
              id: 4,
              title: "SFDSF 8A",
              price: "1233.00",
              desc: "幻夜黑",
              tag: [
                {
                  name: "内存3GB"
                },
                {
                  name: "Micro USB接口"
                }
              ],
              thumb: "https://img.yzcdn.cn/vant/ipad.jpeg"
            }
          ]
        break;
      }
    },
    buy(index) {
      this.show = true
      this.goods = {
        picture: "https://img.yzcdn.cn/vant/ipad.jpeg"
      }
      this.sku = {
        tree: [
          {
            k: "规格",
            v: [
              {
                id: 1,
                name: "32GB",
                imgUrl: "https://img.yzcdn.cn/vant/apple-2.jpg",
                previewImgUrl: "https://img.yzcdn.cn/vant/apple-2.jpg"
              },
              {
                id: 2,
                name: "64GB",
                imgUrl: "https://img.yzcdn.cn/vant/apple-3.jpg",
                previewImgUrl: "https://img.yzcdn.cn/vant/apple-3.jpg"
              }
            ],
            k_s: "s1"
          }
        ],
        list: [
          {
            s1:1,
            price: 280000,
            stock_num: 5
          },
          {
            s1: 2,
            price: 320000,
            stock_num: 5
          }
        ],
        price: "2800.00",
        stock_num: 10,
        none_sku: false,
        hide_stock: false
      }
    },
    onBuyClicked(item) {
      // 传输数量和类型给addressLis
      this.$store.state.specsId = item.selectedSkuComb.s2
      this.$store.state.quantity = item.selectedNum
      this.$router.push('/addressList')
    }
  }
}
</script>
