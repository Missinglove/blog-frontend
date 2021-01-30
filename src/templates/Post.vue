
<template>
  <Layout class="">
    <header
      class="masthead"
      :style="{
        backgroundImage: `url(${GRIDSOME_API_URL + $page.post.cover.url})`,
      }"
    >
      <div class="overlay"></div>
      <div class="container">
        <div class="row">
          <div class="col-lg-8 col-md-10 mx-auto">
            <div class="post-heading">
              <h1>{{ $page.post.title }}</h1>
              <!-- <h2 class="subheading">
                Problems look mighty small from 150 miles up
              </h2> -->
              <span class="meta"
                >Posted by
                <a href="#">Start Bootstrap</a>
                {{ $page.post.created_at }}</span
              >
            </div>
          </div>
        </div>
      </div>
    </header>
    <article>
      <div class="container">
        <div class="row">
          <div class="col-lg-8 col-md-10 mx-auto">
            <p v-html="mdTohtml($page.post.content)"></p>
          </div>
        </div>
      </div>
    </article>
  </Layout>
</template>
<page-query>
query ($id:ID!) {
 post: strapiPost (id:$id){
    id
    title
    content
    cover{
      url
    }
     created_at
    tags {
      id
      title
    }
  }
}

</page-query>
<script>
import Markdowm from "markdown-it";
const md = new Markdowm();
export default {
  nameL: "postPage",
  components: {},
  data() {
    return {};
  },
  computed: {},
  methods: {
    mdTohtml(Markdowm) {
      return md.render(Markdowm);
    },
  },
  mounted() {},
};
</script>

<style lang='css' scoped>
</style>