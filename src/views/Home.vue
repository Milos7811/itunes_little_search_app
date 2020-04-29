<template>
	<section class="home">
		<img alt="Vue logo" src="../assets/vuelogo.png" />

		<hello-world msg="Hot Vue.js App" />
	</section>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/home/HelloWorld.vue'

export default {
	name: 'home',
	components: {
		HelloWorld
	}
}
</script>

<style scoped lang="scss">
img {
	width: 45%;
}
</style>
