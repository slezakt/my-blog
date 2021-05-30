<template>
	<div>
		<section v-if="post">
			<nuxt-content :document="post" />
		</section>
		<NuxtLink to="/">Home</NuxtLink>
	</div>
</template>
<script>
export default {
	async asyncData({ $content, params, error }) {
		let post;
		try {
			post = await $content('blog', params.blog).fetch();
		} catch (e) {
			error({ message: "Stránka neexistuje" });
		}
		return { post }
	}
}
</script>