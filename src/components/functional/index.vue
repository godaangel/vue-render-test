<!-- 
functional示例，functional相当于一个纯函数一样，内部不存储用于在界面上展示的数据，传入什么，展示什么，传入的是相同的数据，展示的必然是相同的。无实例，无状态，没有this上下文，均通过context来控制。

具体使用方式还在摸索中，目前见过的有可以用来做通用动画，如下。

官网介绍用到的地方：（示例见WiiChooseComp组件）
	1、程序化地在多个组件中选择一个
	2、在将 children, props, data 传递给子组件之前操作它们
 -->
<script>
	import Velocity from 'velocity-animate'
	export default {
	  name: 'wii-functional',
	  functional: true,
	  render: function(createElement, context) {
	    let data = {
	      props: {
	        tag: 'ul',
	        css: false
	      },
	      on: {
	        beforeEnter: function(el) {
	          el.style.opacity = 0
	          el.style.height = 0
	        },
	        enter: function(el, done) {
	          let delay = el.dataset.index * 150
	          setTimeout(function() {
	            Velocity(el, {
	              opacity: 1,
	              height: '1.6em'
	            }, {
	              complete: done
	            })
	          }, delay)
	        },
	        leave: function(el, done) {
	          let delay = el.dataset.index * 150
	          setTimeout(function() {
	            Velocity(el, {
	              opacity: 0,
	              height: 0
	            }, {
	              complete: done
	            })
	          }, delay)
	        }
	      }
	    }
	    return createElement('transition-group', data, context.children)
	  }
	}
</script>

<style>
	
</style>