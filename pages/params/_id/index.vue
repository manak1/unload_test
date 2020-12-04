<template>
  <div class="pt-10">
    <h2 class="text-4xl">Params使用パターン</h2>
    <p class="text-2xl mt-5">現在のID {{ getCurrentId }}</p>
    <div class="space-x-6 mt-10">
      <a
        href="#"
        @click.prevent="previousPage"
        class="inline-block rounded border-2 p-2 border-blue-200"
      >
        前のページへ
      </a>
      <a
        href="#"
        @click.prevent="nextPage"
        class="inline-block rounded border-2 p-2 border-blue-200"
      >
        次のページへ
      </a>
    </div>
    <div class="mt-10 space-x-5">
      <nuxt-link to="/" class="text-blue-700 underline">
        トップへ戻る(nuxt-linkタグ)
      </nuxt-link>

      <a href="/" class="text-blue-700 underline">
        トップへ戻る(aタグ)
      </a>
    </div>

    <article class="mt-10 w-2/3 mx-auto">
      <p>
        リロード、ページを閉じる、別ページに遷移しようとするとbeforeunloadによって警告が表示されますが、
        nuxt-linkを使った遷移、$router.push,
        $router.replaceなどrouterを使用した遷移時には警告が表示されません。
      </p>
    </article>
  </div>
</template>

<script>
export default {
  mounted() {
    window.addEventListener("beforeunload", this.confirm);
  },
  methods: {
    confirm(event) {
      event.preventDefault();

      // IEのみメッセージを変更できます。
      event.returnValue = "";
    },

    nextPage() {
      this.$router.push(`/params/${Number(this.getCurrentId) + 1}`);
    },

    previousPage() {
      if (this.getCurrentId > 0) {
        this.$router.push(`/params/${Number(this.getCurrentId) - 1}`);
      }
    }
  },
  mounted() {
    window.addEventListener("beforeunload", this.confirm);
  },

  destroyed() {
    window.removeEventListener("beforeunload", this.confirm)
  },

  computed: {
    getCurrentId() {
      return this.$route.params.id;
    }
  }
};
</script>

<style lang="scss" scoped></style>
