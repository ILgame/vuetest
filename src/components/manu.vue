<template>
  <div>
    <!-- <v-card flast>
      <v-row>
        <v-col>
          <v-card class="mx-7 my-5" width="50%">
            <v-row class="text-center">
              <v-col>
                <v-btn icon outlined x-large>1</v-btn>
              </v-col>
              <v-col>
                <v-btn icon outlined x-large>2</v-btn>
              </v-col>
            </v-row>
            <v-row class="text-center">
              <v-col>
                <v-btn icon outlined x-large>5</v-btn>
              </v-col>
              <v-col>
                <v-btn icon outlined x-large>10</v-btn>
              </v-col>
            </v-row>
          </v-card>
        </v-col>

        <v-col>
          <v-card class="mx-7 my-5" width="50%" >
            <v-row class="text-center">
              <v-card-title>
                coin
                <span class="mx-7">50</span>
                &#3647;
              </v-card-title>
            </v-row>
          </v-card>
        </v-col>
      </v-row>
    </v-card> -->

    <v-row>
      <v-col cols="8" md="8">
        <v-card class="mx-7 my-7" :elevation="10">
          <v-row class="mx-8 my-8">
            <v-col div v-for="item in product" :key="item.id">
              <v-card class="d-inline-block mx-auto" :elevation="10">
                <v-img :src="item.image" height="200px"></v-img>

                <v-card-title>
                  {{ item.name }}
                </v-card-title>

                <v-card-subtitle> {{ item.price }} &#3647; </v-card-subtitle>

                <v-card-actions>
                  <v-btn
                    rounded
                    color="#ffc107"
                    @click="pay(item.name, item.price, item.in_stock)"
                    style=""
                  >
                    Buy
                  </v-btn>
                </v-card-actions>
              </v-card>
            </v-col>
          </v-row>
        </v-card>
      </v-col>

      <v-col cols="4" md="4">
        <v-row>
          <v-col>
            <v-card
              class="mx-7 my-5"
              width="85%"
              height="200px"
              :elevation="10"
            >
              <v-row>
                <v-card-title class="coins">
                  <v-row>
                    <v-col lg="12">
                      <span class="mx-8"
                        >เหรียญที่รับมา : {{ coin }}</span
                      ></v-col
                    ></v-row
                  >
                  <v-row>
                    <v-col lg="12">
                      <h4>
                        <span class="mx-8">รวม : {{ totalCoin }}&#3647;</span>
                      </h4></v-col
                    ></v-row
                  >
                  <v-row>
                    <v-col lg="12">
                      <h4>
                        <span class="mx-8"
                          >เหรียญที่เหลือ : {{ changeCoin }}</span
                        >
                      </h4></v-col
                    ></v-row
                  >
                  <v-row>
                    <v-col lg="12">
                      <h4>
                        <span class="mx-8"
                          >สินค้าที่เลือก : {{ productName }}</span
                        >
                      </h4></v-col
                    ></v-row
                  >
                </v-card-title>
              </v-row>
            </v-card>
          </v-col>
        </v-row>
        <v-row>
          <v-col>
            <v-card class="mx-7 my-5 coins_number" width="85%" :elevation="10">
              <v-row class="text-center">
                <v-col>
                  <v-btn
                    pill
                    @click="insertCoin(10)"
                    class="font-weight-black"
                    fab
                    dark
                    x-large
                    color="#ffcb60"
                    >10</v-btn
                  >
                </v-col>
                <v-col>
                  <v-btn
                    pill
                    @click="insertCoin(5)"
                    class="font-weight-black"
                    fab
                    dark
                    x-large
                    color="#f0e84f"
                    >5</v-btn
                  >
                </v-col>
              </v-row>
              <v-row class="text-center">
                <v-col>
                  <v-btn
                    pill
                    @click="insertCoin(2)"
                    class="font-weight-black"
                    fab
                    dark
                    x-large
                    style="background: linear-gradient(to bottom, rgba(255,255,255,0.15) 0%, rgba(0,0,0,0.15) 100%), radial-gradient(at top center, rgba(255,255,255,0.40) 0%, rgba(0,0,0,0.40) 120%) #989898;
                    background-blend-mode: multiply,multiply;"
                    >2</v-btn
                  >
                </v-col>
                <v-col>
                  <v-btn
                    pill
                    @click="insertCoin(1)"
                    class="font-weight-black"
                    fab
                    dark
                    x-large
                    style="background-image: linear-gradient(to left, #BDBBBE 0%, #9D9EA3 100%), radial-gradient(88% 271%, rgba(255, 255, 255, 0.25) 0%, rgba(254, 254, 254, 0.25) 1%, rgba(0, 0, 0, 0.25) 100%), radial-gradient(50% 100%, rgba(255, 255, 255, 0.30) 0%, rgba(0, 0, 0, 0.30) 100%);
                    background-blend-mode: normal, lighten, soft-light"
                    >1</v-btn
                  >
                </v-col>
              </v-row>
            </v-card>
          </v-col>
        </v-row>
        <v-row>
          <v-btn pill class="re" x-large rounded @click="refund()">clear</v-btn>
        </v-row>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  data() {
    return {
      coin: [],
      changeCoin: [],
      in_stock: Boolean,
      product: [],
      productName: "",
      remain: 0,
      totalCoin: 0,
    };
  },
  mounted() {
    this.fetch();
  },
  methods: {
    fetch() {
      this.product = [];
      this.axios
        .get("v2/5c77c5b330000051009d64c9")
        .then((response) => {
          this.product = response.data.data;
          console.log(response.data);
        })
        .catch((err) => {
          console.log(err.response);
        });
    },
    insertCoin(res) {
      this.coin.push(res);
      this.totalCoin = res + this.totalCoin;
    },
    pay(name, price, in_stock) {
      // check stock
      //set changeCoin=0
      this.changeCoin = [];
      if (in_stock == true) {
        // check totalCoin > price
        if (this.totalCoin >= price) {
          this.totalCoin = this.totalCoin - price;
          this.remain = this.totalCoin;
          this.productName = name;
          //ทอนเงิน
          while (this.remain > 0) {
            if (this.remain >= 10) {
              this.changeCoin.push(10);
              this.remain = this.remain - 10;
              this.totalCoin = 0;
              this.coin = [];
            } else if (this.remain >= 5) {
              this.changeCoin.push(5);
              this.remain = this.remain - 5;
              this.totalCoin = 0;
              this.coin = [];
            } else if (this.remain >= 2) {
              this.changeCoin.push(2);
              this.remain = this.remain - 2;
              this.totalCoin = 0;
              this.coin = [];
            } else if (this.remain >= 1) {
              this.changeCoin.push(1);
              this.remain = this.remain - 1;
              this.totalCoin = 0;
              this.coin = [];
            } else {
              this.remain = 0;
            }
          }
        } else {
          this.productName = "not enough money";
        }
      } else {
        this.productName = "out of stock";
      }
    },
    refund() {
      this.changeCoin = this.coin;
      this.totalCoin = 0;
      this.productName = this.name;
      this.coin = [];
    },
  },
};
</script>

<style>
.v-card__title.coins {
  align-items: center;
  display: flex;
  flex-wrap: wrap;
  font-weight: 500;
  letter-spacing: 0.0125em;
  line-height: 1rem;
  word-break: break-all;
  margin-left: auto;
  margin-right: auto;
  font-size: 30px;
  color: #fdd835;
}
.v-btn__content {
  align-items: center;
  color: inherit;
  display: flex;
  flex: 1 0 auto;
  justify-content: inherit;
  line-height: normal;
  position: relative;
  color: black;
  font-size: 20px;
  /* font-color: black; */
}
.col-md-8.col-8 {
  background: #fafafa;
}
.mx-7.my-7.v-card.v-sheet.theme--light {
  background-image: linear-gradient(to top, #e6e9f0 0%, #eef1f5 100%);
}
.col-md-4.col-4 {
  background: #fafafa;
}
.mx-7.my-5.v-card.v-sheet.theme--light {
  margin-top: 20px;
  margin-bottom: 20px;
  background-image: linear-gradient(to top, #e6e9f0 0%, #eef1f5 100%);
}
.v-btn:not(.v-btn--round).v-size--x-large {
  height: 52px;
  min-width: 92px;
  padding: 0 23.1111111111px;
  margin-left: auto;
  margin-right: auto;
  background: linear-gradient(to bottom, #d5dee7 0%, #e8ebf2 50%, #e2e7ed 100%),
    linear-gradient(
      to bottom,
      rgba(0, 0, 0, 0.02) 50%,
      rgba(255, 255, 255, 0.02) 61%,
      rgba(0, 0, 0, 0.02) 73%
    ),
    linear-gradient(33deg, rgba(255, 255, 255, 0.2) 0%, rgba(0, 0, 0, 0.2) 100%);
  background-blend-mode: normal, color-burn;
  color: #3f3f3f;
}
</style>
