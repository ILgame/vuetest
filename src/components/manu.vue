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
      <v-col cols="12" md="8">
        <v-card class="mx-7 my-7">
          <v-row class="mx-8 my-8">
            <v-col div v-for="item in product" :key="item.id">
              <v-card class="d-inline-block mx-auto">
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

      <v-col cols="12" md="4">
        <v-row>
          <v-col>
            <v-card class="mx-7 my-5" width="80%" height="200px">
              <v-row>
                <v-card-title>
                  coin
                  <span class="mx-7">50</span>
                  &#3647;
                </v-card-title>
              </v-row>
            </v-card>
          </v-col>
        </v-row>
        <v-row>
          <v-col>
            <v-card class="mx-7 my-5" width="80%">
              <v-row class="text-center">
                <v-col>
                  <v-btn icon outlined x-large>10</v-btn>
                </v-col>
                <v-col>
                  <v-btn icon outlined x-large>5</v-btn>
                </v-col>
              </v-row>
              <v-row class="text-center">
                <v-col>
                  <v-btn icon outlined x-large>2</v-btn>
                </v-col>
                <v-col>
                  <v-btn icon outlined x-large>1</v-btn>
                </v-col>
              </v-row>
            </v-card>
          </v-col>
        </v-row>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  data() {
    return {
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
  },
};
</script>
