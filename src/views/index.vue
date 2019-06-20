<template>
  <div class="dd">
    <el-container>
      <headers>
        <el-header></el-header>
      </headers>

      <el-container>
        <asides>
          <el-aside></el-aside>
        </asides>

        <el-container>
          <el-main>Main</el-main>
        </el-container>

        <el-aside>Aside</el-aside>
      </el-container>

      <el-footer>Footer</el-footer>
    </el-container>
  </div>
</template>
<script>
import headers from "./headers/index"; //引入组件路径
import asides from "./asides/index"; //引入组件路径
export default {
  components: {
    //注册组件
    headers,
    asides
  },
  methods: {}
};
</script>

<style>
.el-header,
.el-footer {
  background-color: #b3c0d1;
  color: #333;
  text-align: center;
}

.el-aside {
  background-color: #d3dce6;
  color: #333;
  text-align: center;
  line-height: 100%;
}

.el-main {
  background-color: #e9eef3;
  color: #333;
  text-align: center;
}

body > .el-container {
  margin-bottom: 40px;
}

.el-container:nth-child(5) .el-aside,
.el-container:nth-child(6) .el-aside {
  line-height: 660px;
}

.el-container:nth-child(7) .el-aside {
  line-height: 620px;
}
</style>
