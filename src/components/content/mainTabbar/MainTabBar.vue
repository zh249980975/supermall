<template>
  <tab-bar>
      <!-- 可以通过v-for循环将需要的组件进行循环，就不会让代码看起来太过复杂 -->
      <tab-bar-item v-for="(tabbar,index) in tabbars" :key="index" :path="tabbar.path" :activeColor="color">
        <!-- vue2.6.0之后具名插槽就不再使用solt=""的方式了 改用v-slot=""语法糖#需要放在template标签内 -->
        <template #item-icon>
          <img :src="tabbar.imgsrc">
        </template>
        <template #item-active-icon>
          <img :src="tabbar.activeimg">
        </template>
        <template #item-text>
          <div>{{tabbar.title}}</div>
        </template>
      </tab-bar-item>
    </tab-bar>
</template>

<script>
import TabBar from 'components/common/tabbar/TabBar';
import TabBarItem from 'components/common/tabbar/TabBarItem';


export default {
  name:'MainTabBar',
  data() {
    return {
      tabbars: [
        {
          //通过v-bind绑定src地址，vue会将src解析成字符串而非地址，
          //所以需要用require返回绝对地址
          imgsrc: require('assets/img/tabbar/home.svg'),
          activeimg: require('assets/img/tabbar/home_active.svg'),
          title: '首页',
          path: '/home'
        },
        {
          imgsrc: require('assets/img/tabbar/category.svg'),
          activeimg: require('assets/img/tabbar/category_active.svg'),
          title: '分类',
          path: '/category'
        },
        {
          imgsrc: require('assets/img/tabbar/cart.svg'),
          activeimg: require('assets/img/tabbar/cart_active.svg'),
          title: '购物车',
          path: '/cart'
        },
        {
          imgsrc: require('assets/img/tabbar/profile.svg'),
          activeimg: require('assets/img/tabbar/profile_active.svg'),
          title: '我的',
          path: '/profile'
        },
      ],
      color: 'pink'
    }
  },
  components:{
    TabBar,
    TabBarItem
  }
}
</script>

<style scoped>

</style>