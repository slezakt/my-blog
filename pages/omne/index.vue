<template>
	<div>
		<nuxt-content :document="about" />
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
</template>
<script>
export default {
	async asyncData({ $content, error }) {
		let about;
		try {
			about = await $content("about").fetch();
		} catch (e) {
			error({ message: "Stránka neexistuje" });
		}
		return { about, isModalVisible: false, }
	},
	mounted() {
		setTimeout(()=> {
				this.isModalVisible = true;
		},3000)
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