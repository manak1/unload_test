<template>
  <div class="container">
    <h2 class="text-2xl">Unloadテスター</h2>
    <div class="mt-10 space-x-4">
      <nuxt-link to="query" class="border-4 rounded shadow border-red p-4 inline-block hover:opacity-75" >
        query使用
      </nuxt-link>
      <nuxt-link to="params/1" class="border-4 rounded shadow border-red p-4 inline-block hover:opacity-75" >
        params使用
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped></style>
