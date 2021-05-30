<template>
	<div>
		<section v-if="post">
			<nuxt-content :document="post" />
		</section>
	</div>
</template>
<script>
export default {
	async asyncData({ $content, error }) {
		let post;
		try {
			post = await $$content('blog').fetch();
		} catch (e) {
			error({ message: "Stránka neexistuje" });
		}
		return { post }
	}
}
</script>