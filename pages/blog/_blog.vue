<template>
	<div class="container mx-auto">
		<section v-if="post" class="mb-6">
			<nuxt-content :document="post" />
		</section>
		<NuxtLink to="/" class="py-2 px-6 rounded-md inline-flex bg-gradient-to-br from-yellow-400 to-orange-500">Zpět na domovskou stránku</NuxtLink>
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