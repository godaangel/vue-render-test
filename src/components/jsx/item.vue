<script>
export default {
  name: 'wii-jsx-item',
  data() {
    return {}
  },
  props: {
    color: String
  },
  render: function(createElement) {
    // 等价于 <div class="wii-jsx-item"><slot></slot></div>
    return createElement(
      'div', {
        class: 'wii-jsx-item',
        style: {
          color: this.color
        }
      },
      this.$slots.default
    )
  },
  methods: {

  }
}
</script>

<style>
	.wii-jsx-item{
		cursor: pointer;
	}
</style>