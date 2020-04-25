<template>
  <div id="app">
    <el-container style="height: 500px; border: 1px solid #eee">
      <el-container>
        <el-header style="text-align: right; font-size: 12px">
          <el-menu
                  class="el-menu-demo"
                  mode="horizontal"
                  background-color="#545c64"
                  text-color="#fff"
                  active-text-color="#ffd04b">
            <el-menu-item index="1">式神录</el-menu-item>
          </el-menu>
        </el-header>

        <el-main>
          <el-row>
            <el-col :span="3" v-for="(o, index) in list" :key="o._id" :offset="index > 0 ? 2 : 0">
              <el-card :body-style="{ padding: '0px' }">
                <img v-bind:src="o.imgSrc" class="image">
                <div style="padding: 3px;">
                  <span>{{o.shishenName}}</span>
                </div>
              </el-card>
            </el-col>
          </el-row>
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>
  import axios from 'axios'
export default {
  methods: {
    startHacking () {
      this.$notify({
        title: 'It works!',
        type: 'success',
        message: 'We\'ve laid the ground work for you. It\'s time for you to build something epic!',
        duration: 5000
      })
    }
  },
  data () {
    return {
      list: null
    }
  },
  mounted () {
    axios.get('http://127.0.0.1:8080/shishen')
            .then(response => {this.list = response.data; console.log(response.data)})
  }
}
</script>

<style>
#app {
  font-family: Helvetica, sans-serif;
  text-align: center;
}
</style>
