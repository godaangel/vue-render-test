<!-- 
functional示例，程序化地在多个组件中选择一个
如果对一批组件进行同样的操作，则可以用这个functional，类似于加工厂。
在这个示例中，通过props来切换加载不同的组件，并且在props传递给子组件之前操作它，组件内部定义了不同的click事件来展示示例。
 -->
<script>
	export default {
	  name: 'wii-choose-comp',
	  functional: true,
	  props: {
	  	componentName: String
	  },
	  render: function(createElement, context) {
	  	// 给组件加上class
	  	context.data.class = [context.props.componentName]
	  	// 在props传给子组件之前操作它
	  	context.data.props = {
	  		compName: context.props.componentName
	  	}

	  	context.data.nativeOn = {
	  		click() {
	  			alert('我是functional里面统一的点击事件')
	  		}
	  	}
	    return createElement(context.props.componentName, context.data, context.children)
	  }
	}
</script>

<style>
	
</style>