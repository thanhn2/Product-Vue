<template>
  <div id="app" class="container">
    <img alt="Vue logo" src="./assets/logo.png" />
    <div class="row">
      <input
        type="text"
        placeholder="Enter search here..."
        :model="querySearch"
        v-on:keyup.enter="search($event)"
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
    search($event) {
      this.querySearch = $event.target.value;
      this.isSearch = true;
    }
  }
};
</script>

<style>
#app {
  text-align: center;
}
input {
  width: 100%;
}
</style>