<template>
  <div class="home">
    <core-app-bar></core-app-bar>
    <core-View></core-View>

  </div>
</template>

<script>
// @ is an alias to /src


export default {
  name: "Home",
  components: {
    CoreAppBar: () => import("@/components/core/AppBar.vue"),
    CoreView: () => import("@/components/core/View.vue")

  }
};
</script>

<style lang="scss" scoped>
</style>