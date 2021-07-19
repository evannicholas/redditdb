<template>
  <div>
    <div class="post">
        <div class="row">
          <div class="col-1">score</div>
          <div class="col-9">{{post.title}}</div>
          <div class="col-2" style="text-align: right;">/u/{{post.author_fullname}}</div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    post: Object,
  },
};
</script>

<style lang="scss" scoped>
.post{
    background-color: $primary;
    display: block;
    margin: 20px;
    padding: 20px;
}
</style>