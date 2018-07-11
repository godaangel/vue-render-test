<script>
	export default {
		name: 'wii-first',
		data() {
			return {
				msg: '我是变化前的'
			}
		},
		props: {
			level: {
	      type: [Number, String],
	      required: true
	    }
		},
		render: function (createElement) {
			this.$slots.subtitle = this.$slots.subtitle || []
	    return createElement(
	      'h' + this.level,   // tag name 标签名称
	      // this.$slots.default, // 子组件中的slot 单个传递
	      // this.$slots.subtitle,
	      {
	      	nativeOn: {
				    click: this.nativeClickHandler
				  },
	      },
	      [
	      	this.msg,
	      	...this.$slots.default, // 具名slots传递
	      	...this.$slots.subtitle,
	      	createElement('button', {
	      		on: {
					    click: this.clickHandler
					  },
	      	}, '按钮')
	      ]
	    )
	  },
	  methods: {
	  	clickHandler() {
	  		this.msg = '变化以后'
	  		this.$emit('click')
	  	}
	  }
	}
</script>

<style>
	
</style>