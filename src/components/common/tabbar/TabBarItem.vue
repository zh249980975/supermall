<template>
  <div class="tab-bar-item" @click="itemClick">
    <!-- slot使用建议在外层包装一层div，以防止属性被替换掉 -->
    <div v-if="!isActive">
      <slot name="item-icon">notacitve</slot>
    </div>
    <div v-else>
      <slot name="item-active-icon">active</slot>
    </div>
    <div :style="activeStyle">
      <slot name="item-text">title</slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TabBarItem',
  props: {
    path: String,
    activeColor: {
      type: String,
      default: 'black'
    }
  },
  computed: {
    isActive() {
      return this.$route.path.indexOf(this.path) !== -1
    },
    activeStyle() {
      return this.isActive ? { color: this.activeColor } : {}
    }
  },
  methods: {
    itemClick() {
      this.$router.push(this.path)
    }
  }
}
</script>

<style scoped>
.tab-bar-item {
  flex: 1;
  text-align: center;
  height: 49px;
  font-size: 14px;
  margin-top: 3px;
  vertical-align: middle;
  color: grey
}

.tab-bar-item img {
  height: 24px;
  width: 24px;
}

</style>