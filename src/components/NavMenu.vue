<template>
  <div class="navMenu">
    <template v-for="navMenu in navMenus">
      <el-menu-item v-if="!navMenu.children&&navMenu.entity"
                    :key="navMenu.entity.id"
                    :data="navMenu"
                    :index="navMenu.entity.name"
      >
        <i :class="navMenu.entity.icon"></i>
        <span slot="title">{{navMenu.entity.alias}}</span>
      </el-menu-item>
      <el-submenu v-if="navMenu.children&&navMenu.entity"
                  :key="navMenu.entity.id" :data="navMenu" :index="navMenu.entity.name">
        <template slot="title">
          <i :class="navMenu.entity.icon"></i>
          <span v-show="opened"> {{navMenu.entity.alias}}</span>
        </template>
        <NavMenu :navMenus="navMenu.children"></NavMenu>
      </el-submenu>
    </template>
  </div>
</template>

<script>
export default {
  name: 'NavMenu',
  props: {
    navMenus: {
      type: Array
    },
    opened: {
      type: Boolean,
      default: true
    }
  },
  data () {
    return {}
  },
  methods: {}
}
</script>

<style scoped>
</style>
