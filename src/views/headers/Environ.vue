<template>
  <div>
    <!-- 弹框内容 -->
    <p>发送模块出站功率</p>
    <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="150px" class="demo-ruleForm">
      <!--  -->
      <el-form-item label="出站电平" prop="name">
        <el-col :span="12">
          <el-input v-model="ruleForm.name"></el-input>
        </el-col>
        <el-col :span="12" :push="3">
          <el-button type="primary" @click="submitForm">设置</el-button>
        </el-col>
      </el-form-item>
      <!--  -->
      <el-form-item label="测试波束" prop="region">
        <el-select v-model="ruleForm.region" placeholder="请选择活动区域">
          <el-option label="区域一" value="shanghai"></el-option>
          <el-option label="区域二" value="beijing"></el-option>
        </el-select>
      </el-form-item>
      <el-form-item label="波束状态" prop="type">
        <el-checkbox-group v-model="ruleForm.type">
          <el-checkbox label="参照出模拟状态" name="type"></el-checkbox>
        </el-checkbox-group>
      </el-form-item>

      <p>出站电文发送</p>
      <el-form-item label="时延帧数" prop="name">
        <el-col :span="12">
          <el-input v-model="ruleForm.name"></el-input>
        </el-col>
        <el-col :span="12" :push="3">
          <el-button type="primary" @click="onSubmit">设置</el-button>
        </el-col>
      </el-form-item>


      <p>频率控制因数</p>
      <el-form-item label="频度因子控制" prop="name">
        <el-col :span="12">
          <el-input v-model="ruleForm.name"></el-input>
        </el-col>
        <el-col :span="12" :push="3">
          <el-button type="primary" @click="onSubmit">设置</el-button>
        </el-col>
      </el-form-item>

      <p>零值修正</p>
      <el-form-item label="双向时延修正因子" prop="name">
        <el-col :span="12">
          <el-input v-model="ruleForm.name"></el-input>
        </el-col>
        <el-col :span="12" :push="3">
          <el-button type="primary" @click="onSubmit">设置</el-button>
        </el-col>
      </el-form-item>

      <el-form-item label="单向时延修正因子" prop="name">
        <el-col :span="12">
          <el-input v-model="ruleForm.name"></el-input>
        </el-col>
        <el-col :span="12" :push="3">
          <el-button type="primary" @click="onSubmit">设置</el-button>
        </el-col>
      </el-form-item>

      <p>首次捕获时间判断方法</p>
      <el-form-item label prop="resource">
        <el-radio-group v-model="ruleForm.resource">
          <el-radio label="输出锁定指示"></el-radio>
          <el-radio label="解调出正确电文信息"></el-radio>
        </el-radio-group>
      </el-form-item>
      <p>出入站方法修改接口</p>
      <el-form-item label prop="resource">
        <el-radio-group v-model="ruleForm.resource">
          <el-radio label="可修改状态"></el-radio>
          <el-radio label="不可修改状态"></el-radio>
        </el-radio-group>
      </el-form-item>
      <p>增益控制开关</p>
      <el-form-item label prop="resource">
        <el-radio-group v-model="ruleForm.resource">
          <el-radio label="开"></el-radio>
          <el-radio label="关"></el-radio>
        </el-radio-group>
      </el-form-item>
    </el-form>
  </div>
</template>


<script>
  export default {
    components: {},
    data() {
      return {
        dialogVisible: false,
        dialogVisible1: false,
        ruleForm: {
          name: "",
          region: "",
          date1: "",
          date2: "",
          delivery: false,
          type: [],
          resource: "",
          desc: ""
        },
        rules: {
          name: [{
              required: true,
              message: "请输入活动名称",
              trigger: "blur"
            },
            {
              min: 3,
              max: 5,
              message: "长度在 3 到 5 个字符",
              trigger: "blur"
            }
          ],
          region: [{
            required: true,
            message: "请选择活动区域",
            trigger: "change"
          }],
          date1: [{
            type: "date",
            required: true,
            message: "请选择日期",
            trigger: "change"
          }],
          date2: [{
            type: "date",
            required: true,
            message: "请选择时间",
            trigger: "change"
          }],
          type: [{
            type: "array",
            required: true,
            message: "请至少选择一个活动性质",
            trigger: "change"
          }],
          resource: [{
            required: true,
            message: "请选择活动资源",
            trigger: "change"
          }],
          desc: [{
            required: true,
            message: "请填写活动形式",
            trigger: "blur"
          }]
        }
      };
    },
    methods: {
      submitForm() {
        console.log(112)
      },
      resetForm(formName) {
        this.$refs[formName].resetFields();
      },
      onSubmit() {
        console.log(121)
      }
    }
  };

</script>
