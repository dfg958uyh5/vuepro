<template>
  <div>
    <el-form
      :model="ruleForm"
      :rules="rules"
      ref="ruleForm"
      label-width="100px"
      class="demo-ruleForm"
    >
      <el-form-item label="工作模式" prop="region">
        <el-select v-model="ruleForm.region" placeholder="请选择活动区域" size="mini">
          <el-option label="区域一" value="shanghai"></el-option>
          <el-option label="区域二" value="beijing"></el-option>
        </el-select>
      </el-form-item>
      <el-form-item label="载波模式" prop="region">
        <el-select v-model="ruleForm.region" placeholder="请选择活动区域" size="mini">
          <el-option label="区域一" value="shanghai"></el-option>
          <el-option label="区域二" value="beijing"></el-option>
        </el-select>
      </el-form-item>
    </el-form>
    <!--  -->
    <el-tabs v-model="activeName2" type="card">
      <el-tab-pane label="通道一" name="aisle1">
        <aisle1></aisle1>
        <!-- 组件 -->
      </el-tab-pane>
      <el-tab-pane label="通道二" name="aisle2">
        <aisle2></aisle2>
      </el-tab-pane>
      <el-tab-pane label="通道三" name="aisle3">
        <aisle3></aisle3>
      </el-tab-pane>
      <el-tab-pane label="通道四" name="aisle4">
        <aisle4></aisle4>
      </el-tab-pane>
      <el-tab-pane label="通道五" name="aisle5">
        <aisle5></aisle5>
      </el-tab-pane>
    </el-tabs>
  </div>
</template>
<script>
import aisle1 from "./tag/aisle1";
import aisle2 from "./tag/aisle2";
import aisle3 from "./tag/aisle3";
import aisle4 from "./tag/aisle4";
import aisle5 from "./tag/aisle5";
export default {
  components: {
    aisle1,
    aisle2,
    aisle3,
    aisle4,
    aisle5
  },
  data() {
    return {
      activeName2: "aisle1",
      activeName2: "aisle2",
      activeName2: "aisle3",
      activeName2: "aisle4",
      activeName2: "aisle5",
      num8: 1,
      num1: 1,
      ruleForm: {
        region: ""
      },
      rules: {
        region: [
          { required: true, message: "请选择活动区域", trigger: "change" }
        ]
      }
    };
  }
};
</script>
