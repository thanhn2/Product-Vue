<template>
  <div id="app" class="container">
    <div class="text--middle">
      <img alt="Vue logo" src="./assets/logo.png" />
    </div>
    <div class="row col-6 middle">
      <input
        type="text"
        placeholder="Enter search here..."
        :model="querySearch"
        v-on:keyup.enter="search($event.target.value)"
      />
    </div>
    <list-search v-if="isSearch" :querySearch="querySearch" />
  </div>
</template>

<script>
import ListSearch from "./components/ListSearch.vue";

export default {
  name: "App",
  components: {
    ListSearch
  },
  data: function() {
    return {
      querySearch: "",
      isSearch: false
    };
  },
  methods: {
    search(val) {
      this.querySearch = val;
      this.isSearch = true;
    }
  }
};
</script>

<style src="@/assets/css/style.css">
</style>