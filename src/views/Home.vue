<template>
  <div>
    <v-toolbar dark prominent src="">
      <v-row>
        <v-col>
          <v-img
            right
            src="https://www.flaticon.com/svg/static/icons/svg/1027/1027866.svg"
            width="12%"
            height="100%"
            style="margin-right:2rem"
          ></v-img>
        </v-col>
        <v-col lg="3">
          <v-toolbar-title>ตู้จำหน่ายเครื่องดื่ม</v-toolbar-title>
        </v-col>
        <v-col lg="4"></v-col> </v-row
    ></v-toolbar>
    <manu />
  </div>
</template>

<script>
// @ is an alias to /src
import manu from "../components/manu";
export default {
  name: "Home",
  components: {
    manu,
  },
  mounted() {},
  methods: {},
};
</script>

<style>
.v-toolbar--prominent .v-toolbar__title {
  font-size: 40px;
  padding-top: 6px;
  margin-top: 1rem;
}
</style>
