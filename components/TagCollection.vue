<template>
  <ul class="tags">
    <li v-for="tag in tags" :key="tag.id">#{{ tag }}</li>
  </ul>
</template>

<script>
export default {
  name: "TagCollection",
  props: {
    tags: Array,
    require: true,
  },
};
</script>

<style lang="scss" scoped>
.tags {
  list-style: none;
  display: flex;
  justify-content: flex-end;
  li {
    text-decoration: none;
    color: gray;
    &::before {
      white-space: pre-wrap;
      content: " ";
    }
  }
}
</style>