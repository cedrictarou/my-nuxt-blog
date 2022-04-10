<template>
  <section class="text-gray-600 body-font">
    <div
      class="
        container
        mx-auto
        flex
        px-5
        py-24
        md:flex-row
        flex-col
        items-center
      "
    >
      <div class="lg:max-w-lg lg:w-full md:w-1/2 w-5/6 mb-10 md:mb-0">
        <article-image
          :img="article.img"
          class="object-cover object-center rounded"
        />
      </div>

      <div
        class="
          lg:flex-grow
          md:w-1/2
          lg:pl-24
          md:pl-16
          flex flex-col
          md:items-start md:text-left
          items-center
          text-center
        "
      >
        <tag-collection :tags="article.tags" />
        <h1
          class="title-font sm:text-4xl text-3xl mb-4 font-medium text-gray-900"
        >
          {{ article.title }}
        </h1>
        <nuxt-content :document="article" class="mb-8 leading-relaxed" />
      </div>
    </div>
    <footer>
      <page-nation :prev="prev" :next="next" />
    </footer>
  </section>
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
</style>