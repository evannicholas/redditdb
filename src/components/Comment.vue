<template>
  <div v-if="comment != undefined">
    <div class="row comment q-ma-sm q-pa-md">
      <div class="col-1">
        {{ comment.ups }}
      </div>
      <div class="col-11">
        <div class="row author">
          /u/{{ comment.author }}
        </div>
        <div class="row">
          {{ comment.body }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    comment: Object,
  },
};
</script>

<style lang="scss" scoped>
.comment {
  background-color: $dark;
  border-radius: 5px;
}
.author {
   margin-bottom: 10px;
   color: $primary;
   font-weight: bold;
}
</style>