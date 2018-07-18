<!-- 
comp2
 -->
<script>
	export default {
	  name: 'wii-comp-two',
	  props: {
	  	compName: String
	  },
	  render: function(createElement) {
	    return createElement('div', [
	    	'我是第二个comp, 点我试试呗, ',
	    	`我的名字叫${this.compName}, `,
	    	...this.$slots.default
	    ])
	  }
	}
</script>

<style>
	
</style>