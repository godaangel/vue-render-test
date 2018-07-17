<!-- jsx 演示jsx的使用方式

安装依赖 npm install babel-plugin-syntax-jsx babel-plugin-transform-vue-jsx babel-helper-vue-jsx-merge-props babel-preset-env --save-dev

.babelrc配置 "plugins": ["transform-vue-jsx"]

webpack配置 test: /\.jsx?$/

 -->

 <script type="text/jsx">
 	import WiiJsxItem from './item.vue'
	export default {
		name: 'wii-jsx',
		components: {
			WiiJsxItem
		},
		data() {
			return {
				color: 'red'
			}
		},
		props: {
			
		},
		render: function (h) {
	    return (
	    	<div class="wii-jsx">
					<wii-jsx-item color={this.color} nativeOnClick={this.clickHandler}>
		    		<span>我是wii-jsx-item组件的slot, color通过变量传入: {this.color}</span>
		    	</wii-jsx-item>
	    	</div>
	    )
	  },
	  methods: {
	  	clickHandler() {
	  		this.color = this.color == 'red' ? 'blue' : 'red'
				console.log(`点击了wii-jsx-item，通过native触发，改变了颜色为【${this.color}】`)
	  	}
	  }
	}
</script>

<style>
	.wii-jsx{
		margin-top: 15px;
	}
</style>