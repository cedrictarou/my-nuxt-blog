<template>
  <div class="page-nation">
    <hr />
    <div>You may be interested in ...</div>
    <ul>
      <li v-if="prev">
        <NuxtLink :to="prev.slug"> {{ prev.title }} </NuxtLink>
      </li>
      <li v-if="next">
        <NuxtLink :to="next.slug"> {{ next.title }} </NuxtLink>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "PageNation",
  props: ["prev", "next"],
};
</script>

<style lang="scss">
.page-nation {
  margin-top: 40px;
}
.page-nation ul {
  list-style: none;
  display: flex;
  justify-content: space-between;
  li {
    text-decoration: none;
  }
}
</style>