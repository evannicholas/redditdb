<template>
  <div>
    <!-- post -->
    <div v-for="comment in comments" :key="comment.data.permalink">
      <CommentComponents :comment="comment.data"/>
    </div>
  </div>
</template>

<script>
import { api } from "boot/axios";
import CommentComponents from "components/Comment.vue";
export default {
  components: {
    CommentComponents,
  },
  data() {
    return {
      post: {},
      comments: [],
    };
  },
  methods: {
    loadPermalink() {
      const modifiedPermalink = this.$route.params.url;
      const permalink = modifiedPermalink.replaceAll(".", "/");
      console.log(`http://www.reddit.com${permalink}.json`);
      api.get(`http://www.reddit.com${permalink}.json`).then((response) => {
        this.post = response.data[0].data.children[0].data;
        this.comments = response.data[1].data.children;
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