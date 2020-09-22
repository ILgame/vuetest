<template>
  <div>
    <v-toolbar
      dark
      prominent
      src=""
      style="background-image: linear-gradient(to top, #f77062 0%, #fe5196 100%);"
    >
      <v-row>
        <v-col>
          <v-img
            right
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
.v-toolbar--prominent:not(.v-toolbar--bottom) .v-toolbar__title {
  align-self: flex-end;
  padding-bottom: 6px;
  padding-top: 0;
  font-size: 40px;
}
</style>
