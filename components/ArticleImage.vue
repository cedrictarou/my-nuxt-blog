<template>
  <div>
    <img :src="imgSrc" />
  </div>
</template>

<script>
export default {
  name: "ArticleImage",
  props: {
    img: {
      type: String,
      require: true,
    },
  },
  computed: {
    imgSrc() {
      return require(`~/assets/resources/${this.img}`);
    },
  },
};
</script>

<style lang="scss" scoped>
</style>