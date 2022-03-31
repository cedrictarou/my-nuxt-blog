<template>
  <article>
    <article-image :img="article.img" />
    <tag-collection :tags="article.tags" />
    <nuxt-content :document="article" />
    <page-nation :prev="prev" :next="next" />
  </article>
</template>

<script>
import PageNation from "../components/PageNation.vue";
import ArticleImage from "../components/ArticleImage.vue";
import TagCollection from "../components/TagCollection.vue";
export default {
  components: { PageNation, ArticleImage, TagCollection },
  async asyncData({ $content, params }) {
    const article = await $content("blog", params.slug).fetch();
    const [prev, next] = await $content("blog")
      .only(["title", "slug", "tags"])
      .sortBy("title", "asc")
      .surround(params.slug, { before: 1, after: 1 })
      .fetch();
    return { article, prev, next };
  },
};
</script>

<style>
article {
  display: block;
  margin: 0 auto;
  padding: 50px 30px;
  max-width: 800px;
}
h1 {
  font-size: 28px;
  font-weight: 900;
  margin-bottom: 30px;
}
</style>