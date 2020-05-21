<template>
  <ul>
    <li v-for="(item, index) in listResponse" :key="item.id">
      <a
        :href="item.html_url"
        target="_blank"
      >{{ ++index }}. {{ item.name }} - {{ item.description }}</a>
    </li>
  </ul>
</template>

<script>
export default {
  name: "list-search",
  model: {
    prop: "querySearch",
    event: "change"
  },
  props: {
    querySearch: String
  },
  data: function() {
    return {
      listResponse: []
    };
  },
  mounted() {
    this.search();
  },
  watch: {
    querySearch: function(val) {
      this.querySearch = val;
      this.search();
    }
  },
  methods: {
    search() {
      fetch(`https://api.github.com/search/repositories?q=${this.querySearch}`)
        .then(response => response.json())
        .then(json => (this.listResponse = json.items));
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped src="@/assets/css/list-search.css">
</style>
