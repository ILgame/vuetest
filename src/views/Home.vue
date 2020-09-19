<template>
  <div>
    <v-toolbar dark prominent>
      <v-toolbar-title>Vending Machine</v-toolbar-title>
    </v-toolbar>

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
  mounted() {
    this.fetch();
  },
  methods: {
    fetch() {
      this.axios
        .get("v2/5c77c5b330000051009d64c9")
        .then((response) => {
          // console.log(response.data);
        })
        .catch((err) => {
          console.log(err.response);
        });
    },
  },
};
</script>
