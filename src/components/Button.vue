<template>
	<button v-bind:class="className">
		<slot />
	</button>
</template>

<script>
	export default {
		data() {
			return {
				className: `
				btn 
				btn-${this.color ? this.color : 'info'} 
				${this.circle ? 'rounded-circle' : ''}
				shadow-sm
				`
			}
		},
		name: 'Button',
		props: ['circle', 'color'],
	}
</script>