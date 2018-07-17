<!-- 
基础示例 简单的渲染用法
包含 标签，props，slot以及createElement和点击事件
 -->
<script>
	export default {
	  name: 'wii-first',
	  data() {
	    return {
	      msg: 0
	    }
	  },
	  props: {
	    level: {
	      type: [Number, String],
	      required: true
	    }
	  },
	  render: function(createElement) {
	    this.$slots.subtitle = this.$slots.subtitle || []
	      // this.level = 1时, 等价于
	      // <h1 class="wii-first">
	      // 	第一个组件, <slot></slot>
	      // 	<slot name="subtitle"></slot>，此处是data的值: {{msg}}
	      // 	<button @click="clickHandler">点我改变内部data值</button>
	      // </h1>
	    return createElement(
	      'h' + this.level, // tag name 标签名称
	      {
	        class: 'wii-first'
	      },
	      // this.$slots.default, // 子组件中的slot 单个传递
	      // this.$slots.subtitle,
	      [
	        '第一个组件, ',
	        ...this.$slots.default, // 默认slots传递
					...this.$slots.subtitle, // 具名slots传递
	        '，此处是data的值: ',
	        this.msg,
	        createElement('button', {
	          on: {
	            click: this.clickHandler
	          },
	        }, '点我改变内部data值')
	      ]
	    )
	  },
	  methods: {
	    clickHandler() {
	      this.msg = Math.ceil(Math.random() * 1000)
	    }
	  }
	}
</script>

<style>
	.wii-first{
		line-height: 1;
	}
</style>