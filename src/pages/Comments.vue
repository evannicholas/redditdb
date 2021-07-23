<template>
  <div>
    {{ $route.params.url }}
  </div>
</template>

<script>
import { api } from "boot/axios";
export default {
  methods: {
    loadPermalink() {
      const modifiedPermalink = this.$route.params.url;
      const permalink = modifiedPermalink.replaceAll(".", "/");
      console.log(`https://www.reddit.com${permalink}.json`);
        api.get(`https://www.reddit.com${permalink}.json`).then((response) => {
        //   this.posts = response.data.data.children;
        console.log(response.data);
        });
    },
  },
  mounted() {
    this.loadPermalink();
  },
};
</script>

<style lang="scss" scoped>
</style>