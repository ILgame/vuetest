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
                  <v-btn color="purple" text>
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
              width="80%"
              height="200px"
              :elevation="10"
            >
              <v-row>
                <v-card-title class="coins">
                  coin
                  <span class="mx-7">{{ coin || 0 }}</span>
                  &#3647;
                </v-card-title>
              </v-row>
            </v-card>
          </v-col>
        </v-row>
        <v-row>
          <v-col>
            <v-card class="mx-7 my-5 coins_number" width="80%" :elevation="10">
              <v-row class="text-center">
                <v-col>
                  <v-btn
                    class="font-weight-black"
                    fab
                    dark
                    x-large
                    color="#ffcb60"
                    v-on:click="
                      input('10');
                      operater('+');
                    "
                    >10</v-btn
                  >
                </v-col>
                <v-col>
                  <v-btn
                    class="font-weight-black"
                    fab
                    dark
                    x-large
                    color="#f0e84f"
                    v-on:click="
                      input('5');
                      operater('+');
                    "
                    >5</v-btn
                  >
                </v-col>
              </v-row>
              <v-row class="text-center">
                <v-col>
                  <v-btn
                    class="font-weight-black"
                    fab
                    dark
                    x-large
                    style="background: linear-gradient(to bottom, rgba(255,255,255,0.15) 0%, rgba(0,0,0,0.15) 100%), radial-gradient(at top center, rgba(255,255,255,0.40) 0%, rgba(0,0,0,0.40) 120%) #989898;
                    background-blend-mode: multiply,multiply;"
                    v-on:click="
                      input('2');
                      operater('+');
                    "
                    >2</v-btn
                  >
                </v-col>
                <v-col>
                  <v-btn
                    class="font-weight-black"
                    fab
                    dark
                    x-large
                    style="background-image: linear-gradient(to left, #BDBBBE 0%, #9D9EA3 100%), radial-gradient(88% 271%, rgba(255, 255, 255, 0.25) 0%, rgba(254, 254, 254, 0.25) 1%, rgba(0, 0, 0, 0.25) 100%), radial-gradient(50% 100%, rgba(255, 255, 255, 0.30) 0%, rgba(0, 0, 0, 0.30) 100%);
                    background-blend-mode: normal, lighten, soft-light"
                    v-on:click="
                      input('1');
                      operater('+');
                    "
                    >1</v-btn
                  >
                </v-col>
              </v-row>
            </v-card>
          </v-col>
        </v-row>
        <v-row>
          <v-btn class="re" x-large rounded>Reset</v-btn>
        </v-row>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  data() {
    return {
      value: 0,
      coin: 0,
      product: null,
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
    input: function(num) {
      if (num == "." && this.coin.includes(".")) return;
      else if (this.coin == 0) {
        this.coin = num;
        this.value = num;
      } else {
        this.value += num;
        this.coin = this.value;
      }
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
  line-height: 2rem;
  word-break: break-all;
  margin-left: auto;
  margin-right: auto;
  margin-top: 4rem;
  font-size: 45px;
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
  font-color: black;
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
