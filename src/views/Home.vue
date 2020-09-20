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
  mounted() {},
  methods: {},
};
</script>
