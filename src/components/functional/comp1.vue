<!-- 
comp1
 -->
<script>
	export default {
	  name: 'wii-comp-one',
	  props: {
	  	compName: String
	  },
	  render: function(createElement) {
	    return createElement('div', [
	    	'我是第一个comp, 我有点击效果, ',
	    	`我的名字叫${this.compName}, `,
	    	...this.$slots.default
	    ])
	  }
	}
</script>

<style>
	
</style>