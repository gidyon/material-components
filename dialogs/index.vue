<template>
	<div id="dialog" class="fixed fh fw" v-if="showDialog">
		<div class="fw fh dialog-wrapper" @blur="hideDialog">
			<div class="fw fh flex j-c_center a-i_center">
				<div class="f-f_cn a-i_center j-c_fstart" id="card-element" role="dialog">
					<div class="fw">
						<div class="fw flex a-i_center btn-close-area">
							<button class="btn-close f-f_rn j-c_center a-i_center" @click="hideDialog">
								<i class="material-icons md-primary md-24 md-hover">close</i>
							</button>
						</div>
					</div>
					<keep-alive>
						<component :is="componentName"></component>		
					</keep-alive>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
	import {mapGetters} from 'vuex';
	import Login from '@/components/auth/login';
	import SignUp from '@/components/auth/signup';

	export default {
		computed: {			
			...mapGetters([
				'showDialog',
				'dialogCompName',
			]),
			componentName() {
				return this.dialogCompName.substr(18)
			}
		},
		components: {
			'login': Login,
			'signup': SignUp,
		},		
		methods: {
			hideDialog() {
				console.log(this.compName)
				this.$store.commit('showDialog', false)
			}
		},
	};
</script>

<style lang="scss" scoped>
	#dialog{
		position: fixed !important;
		z-index: 20;
		top: 0px !important;
		right: 0px !important;
		bottom: 0px !important;
		left: 0px !important;
		height: 100%;
		overflow-y: auto !important;
		background-color: rgba(0, 0, 0, 0.7);
		.dialog-wrapper{
			padding-top: 64px; 
			padding-bottom: 64px; 
			display: table !important;
		}
		.btn-close-area{
			padding: 15px;
		}
		#card-element{
			min-height: 400px;
			width: 40%;
			background-color: white;
		}
	}
</style>

