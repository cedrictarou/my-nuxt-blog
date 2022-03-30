<template>
  <article>
    <nuxt-content :document="article" />
    <page-nation :prev="prev" :next="next" />
  </article>
</template>

<script>
import PageNation from "../components/PageNation.vue";
export default {
  components: { PageNation },
  async asyncData({ $content, params }) {
    const article = await $content("blog", params.slug).fetch();
    const [prev, next] = await $content("blog")
      .only(["title", "slug"])
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