<!-- 
	主要展示render中createElement的配置slot属性用法，
	因为此处一直很疑惑什么情况下能够用到这个slot属性，所以就试了一下，仅供参考，具体使用场景需要根据业务逻辑来定
 -->
<script>
export default {
  name: 'wii-third',
  data() {
    return {}
  },
  components: {
    WiiTestSlot: {
      name: 'wii-test-slot',
      render(createElement) {
        this.$slots.testslot = this.$slots.testslot || []
          // 等价于
          // <div>
          // 	第三个组件，测试在组件中定义slot, <slot name="testslot"></slot>
          // </div>
        return createElement(
          'div', [
            '第三个组件，测试在组件中定义slot, ',
            ...this.$slots.testslot
          ]
        )
      }
    },
    WiiTestSlotIn: {
      name: 'wii-test-slot-in',
      render(createElement) {
        // 等价于
        // <span>我是组件中的slot内容</span>
        return createElement(
          'span', [
            '我是组件中的slot内容'
          ]
        )
      }
    }
  },
  props: {

  },
  render: function(createElement) {
    // 等价于
    // <div style="margin-top: 15px;">
    // 	<wii-test-slot>
    // 		<wii-test-slot-in slot="testslot"></wii-test-slot-in>
    // 	</wii-test-slot>
    // </div>
    return createElement(
      'div', {
        style: {
          marginTop: '15px'
        }
      }, [
        createElement(
          'wii-test-slot',
          //这么写不会被渲染到节点中去
          // createElement(
          //    'wii-test-slot-in',
          //    {
          //      slot: 'testslot'
          //    }
          //  ),
          [
            // createElement再放createElement需要放入数组里面，建议所有的组件的内容都放到数组里面，统一格式，防止出错
            createElement(
              'wii-test-slot-in', {
                slot: 'testslot'
              }
            )
          ]
        )
      ]
    )
  },
  methods: {

  }
}
</script>

<style>
	
</style>