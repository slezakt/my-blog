<template>
  <div class="">
    <div class="w-full bg-gradient-to-br from-purple-500 to-indigo-500 p-8 text-white">
      <div class="container mx-auto">
        <h1 class="text-4xl">
          Tomův webdev blog
        </h1>
      </div>
    </div>
    <div class="container mx-auto">
      <ul class="flex justify-between">
        <li v-for="post of posts" :key="post.slug" class="w-1/2 m-2">
          <NuxtLink :to="`blog/${post.slug}`" class="flex flex-col bg-white p-6 rounded-lg shadow-md">
            <p>{{ post.date }}</p>
            <h3>{{ post.title }}</h3>
            <p>{{ post.description }}</p>
            <img :src="post.thumbnail" alt="" />
          </NuxtLink>
        </li>
      </ul>
      <button
        type="button"
        class="btn"
        @click="showModal"
      >
        Open Modal!
      </button>

      <Modal
        v-show="isModalVisible"
        @close="closeModal"
      >
        <template v-slot:header>
          This is a new modal header.
        </template>

        <template v-slot:body>
          This is a new modal body.
        </template>

        <template v-slot:footer>
          This is a new modal footer.
        </template>
      </Modal>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, error }) {
    let posts;
    try {
      posts = await $content('blog').fetch();
    } catch (e) {
      error({ message: "Stránka neexistuje" });
    }
    return { posts }
  },
  data() {
      return {
        isModalVisible: false,
      };
    },
    methods: {
      showModal() {
        this.isModalVisible = true;
      },
      closeModal() {
        this.isModalVisible = false;
      }
    }
}
</script>

<style>
</style>
