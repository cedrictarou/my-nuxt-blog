<template>
  <div class="container mx-auto max-w-4xl min-w-min">
    <h1 class="text-center text-4xl">Test Page</h1>
    <!-- container -->
    <div class="bg-green-50">
      <div class="flex flex-col md:flex-row">
        <img
          class="block max-w-max md:w-1/3 container mx-auto"
          src="https://placehold.jp/300x300.png"
        />

        <div class="w-full md:w-3/2 flex flex-col justify-center">
          <h3 class="text-2xl text-center pt-5">title</h3>
          <p class="text-lg text-gray-500 flex p-5">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Veniam
            perspiciatis quasi dolorum ea recusandae voluptate, repellendus
            voluptas ipsa laudantium doloribus vitae deleniti nam, totam quidem
            iusto veritatis quam amet culpa!
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "test",
};
</script>

<style lang="scss" scoped>
.image {
  max-width: 100%;
  height: auto;
}
</style>