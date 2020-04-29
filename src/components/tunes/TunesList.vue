<template>
	<ul class="tunes-list">
		<transition-group tag="li" name="fade">
			<tunes-song v-for="song in songs" :key="song.id" :song="song" />
		</transition-group>
		<div class="moreButton" v-on:click="moreMusic" v-if="isEmpty === true">
			More
		</div>
	</ul>
</template>

<script>
import TunesSong from '@/components/tunes/TunesSong.vue'

export default {
	components: {
		TunesSong
	},
	data() {
		return {
			songs: [],
			isEmpty: false
		}
	},
	mounted() {
		this.$root.$on(
			'new-songs-arrived',
			data => ((this.songs = data), this.haveSong())
		)
	},
	methods: {
		haveSong() {
			if (this.songs.length === 0) {
				return (this.isEmpty = false)
			} else {
				return (this.isEmpty = true)
			}
		},
		moreMusic() {
			this.$root.$emit('generate-music', this.isEmpty)
		}
	}
}
</script>

<style lang="scss" scoped>
ul {
	margin-top: 3em;
	padding-left: 0;
	list-style: none;
}
.moreButton {
	width: 60px;
	height: 60px;
	margin: auto;
	color: aqua;
	background-color: white;
	border-radius: 50%;
	line-height: 60px;
	cursor: pointer;
}
.fade-enter,
.fade-leave-to {
	transform: scale(0.9);
}
.fade-enter-active,
.fade-leave-active {
	transition: all 0.1s ease-in;
}
</style>
