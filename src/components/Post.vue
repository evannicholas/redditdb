<template>
  <div>
    <div class="post">
      <div class="row">
        <div class="col-1" style="text-align: center">
          <div class="row">
            <div class="col">
              <q-btn color="secondary" icon="thumb_up_off_alt" label="" />
            </div>
          </div>
          <div class="row">
            <div class="col">
              {{ post.ups }}
            </div>
          </div>
        </div>
        <div class="col-9">
          <div class="row">
            <div class="col">
              <a target="_blank" :href="post.url">{{ post.title }}</a>
            </div>
          </div>
          <div class="row" v-if="post.post_hint == 'image'">
            <div class="col">
              <q-img
                :src="post.url"
                fit="contain"
                position="0 0"
                height="300px"
                spinner-color="primary"
                spinner-size="82px"
              />
            </div>
          </div>
          <div class="row" v-else>
            <div class="col">
              <a class="weblink" :href="post.url"><q-icon name="link" /> {{ post.url }}</a>
            </div>
          </div>
          <!-- <div
            class="row"
            v-if="
              post.post_hint == 'rich:video' || post.post_hint == 'hosted:video'
            "
          >
            <div class="col">
              <q-video :ratio="16 / 9" :src="post.url" />
            </div>
          </div> -->
        </div>
        <div class="col-1">
          <q-btn
            :to="'/comments/' + modifiedPermalink"
            color="secondary"
            icon="comment"
            label=""
          />
          <!-- <q-btn
            type="a"
            target="_blank"
            :href="'https://reddit.com/' + post.permalink"
            color="secondary"
            icon="comment"
            label=""
          /> -->
        </div>
        <div class="col-1" style="text-align: right">
          <a
            target="_blank"
            :href="'https://www.reddit.com/user/' + post.author"
          >
            /u/{{ post.author }}</a
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    post: Object,
  },
  computed: {
    modifiedPermalink() {
      const permalink = this.post.permalink;
      return permalink.replaceAll('/', ".");
    }
  },
};
</script>

<style lang="scss" scoped>
.post {
  background-color: rgb(80, 75, 75);
  display: block;
  margin: 20px;
  padding: 20px;
  border-radius: 10px;
}
a {
  color: white;
  text-decoration: none;
}
.weblink {
  color: rgb(28, 181, 231);
}
</style>