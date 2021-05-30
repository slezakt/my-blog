<template>
	<div>
		<nuxt-content :document="about" />
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
		return { about }
	}
}
</script>