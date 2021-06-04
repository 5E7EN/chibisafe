<template>
	<div>
		<div class="root">
			<div class="mainBlock">
				<div>
					<h4>5E7EN File Uploader</h4>
					<div class="mt4" />
					<Uploader v-if="config.publicMode || (!config.publicMode && loggedIn)" />
					<div
						v-else
						class="is-size-4">
						Powered by
						<a href="https://github.com/WeebDev/chibisafe" target="_blank">
							chibisafe
						</a>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>
<script>
import { mapState, mapGetters } from 'vuex';

import Uploader from '~/components/uploader/Uploader.vue';

export default {
	name: 'Home',
	components: {
		Uploader
	},
	data() {
		return { albums: [] };
	},
	computed: {
		...mapGetters({ loggedIn: 'auth/isLoggedIn' }),
		...mapState(['config'])
	},
	head() {
		return {
			title: 'Home'
		};
	}
};
</script>
<style lang="scss" scoped>
	.root {
		width: 56%;
		position: relative;
		.mainBlock {
			height: calc(100vh - 52px);
			position: relative;
			margin: 0 5rem;
			> div {
				position: absolute;
				top: 25%;
			}
		}
		p {
			font-size: 1.25em;
			margin-top: 1rem;
		}
		strong {
			text-decoration: underline;
		}
	}

	@media (max-width: 1025px) {
		.root {
			width: 100%;
			.mainBlock {
				height: auto;
				padding: 2rem 0;
				> div {
					top: 0rem;
					position: relative;
					text-align: center;
				}
			}
		}
	}
</style>
