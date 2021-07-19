<template>
  <div>
    <div v-for="post in posts" :key="post.data.permalink">
      <!-- {{post.data.title}}
      {{post.data.author_fullname}} -->
      <Post :post="post.data"> </Post>
    </div>
  </div>
</template>

<script>
import { api } from "boot/axios";
import Post from "components/Post.vue";
export default {
  components: {
    Post,
  },
  data() {
    return {
      posts: [],
    };
  },
  methods: {
    loadData() {
      api.get("https://www.reddit.com/.json").then((response) => {
        this.posts = response.data.data.children;
      });
    },
  },
  mounted() {
    this.loadData();
  },
};
</script>

<style lang="scss" scoped>
</style>