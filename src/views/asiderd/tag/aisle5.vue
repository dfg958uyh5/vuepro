<template>
  <div>
    <el-form
      :model="ruleForm"
      :rules="rules"
      ref="ruleForm"
      label-width="100px"
      class="demo-ruleForm"
    >
      <!--  -->
      <el-form-item label="载波频偏" prop="name">
        <el-col :span="6">
          <el-input v-model="ruleForm.name" size="mini"></el-input>
        </el-col>
        <el-col :span="6" :push="1">
          <el-radio-group v-model="ruleForm.resource">
            <el-radio label="关闭该通道"></el-radio>
          </el-radio-group>
        </el-col>
        <el-col :span="6" :push="3">
          <el-button type="primary" size="mini">ALL</el-button>
        </el-col>
      </el-form-item>
      <!--  -->
      <p>功能设置</p>
      <el-form-item label="I支路功率" prop="name">
        <el-col :span="6">
          <el-input v-model="ruleForm.name" size="mini"></el-input>
        </el-col>
        <el-col :span="6" :push="3">
          <el-button type="primary" size="mini">ON</el-button>
        </el-col>
        <el-col :span="6" :push="3">
          <el-button type="primary" size="mini">ALL</el-button>
        </el-col>
      </el-form-item>
      <el-form-item label="Q支路功率" prop="name">
        <el-col :span="6">
          <el-input v-model="ruleForm.name" size="mini"></el-input>
        </el-col>
        <el-col :span="6" :push="3">
          <el-button type="primary" size="mini">OFF</el-button>
        </el-col>
        <el-col :span="6" :push="3">
          <el-button type="primary" size="mini">ALL</el-button>
        </el-col>
      </el-form-item>
      <!--  -->
      <P>伪距变化模型</P>
      <el-form-item prop="name">
        <el-col :span="8">
          <el-radio-group v-model="ruleForm.resource">
            <el-radio label="直线运动"></el-radio>
          </el-radio-group>
        </el-col>
        <el-col :span="8">
          <el-radio-group v-model="ruleForm.resource">
            <el-radio label="正炫运动"></el-radio>
          </el-radio-group>
        </el-col>
        <el-col :span="4">
          <el-button type="primary" size="mini">ALL</el-button>
        </el-col>
      </el-form-item>
      <!--  -->
      <p>模型参数</p>
      <el-form-item label="活动名称" prop="name">
        <el-input v-model="ruleForm.name" size="mini"></el-input>
      </el-form-item>
      <el-form-item label="活动名称" prop="name">
        <el-input v-model="ruleForm.name" size="mini"></el-input>
      </el-form-item>
      <el-form-item label="活动名称" prop="name">
        <el-input v-model="ruleForm.name" size="mini"></el-input>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="onSubmit" size="mini">提交</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>


<script>
export default {
  components: {},
  data() {
    return {
      num8: 1,
      num1: 1,
      ruleForm: {
        name: "",
        date1: "",
        date2: "",
        delivery: false,
        type: [],
        resource: "",
        desc: "",
        newsList: []
      },
      rules: {
        name: [
          { required: true, message: "请输入活动名称", trigger: "blur" },
          { min: 3, max: 5, message: "长度在 3 到 5 个字符", trigger: "blur" }
        ],
        date1: [
          {
            type: "date",
            required: true,
            message: "请选择日期",
            trigger: "change"
          }
        ],
        date2: [
          {
            type: "date",
            required: true,
            message: "请选择时间",
            trigger: "change"
          }
        ],
        type: [
          {
            type: "array",
            required: true,
            message: "请至少选择一个活动性质",
            trigger: "change"
          }
        ],
        resource: [
          { required: true, message: "请选择活动资源", trigger: "change" }
        ],
        desc: [{ required: true, message: "请填写活动形式", trigger: "blur" }]
      }
    };
  },
  created() {
    // this.dataList();
  },
  methods: {
    handleChange(value) {
      console.log(value);
    },
    submitForm(formName) {
      this.$refs[formName].validate(valid => {
        if (valid) {
          alert("submit!");
        } else {
          console.log("error submit!!");
          return false;
        }
      });
    },
    onSubmit() {
      console.log("submit!");
    },
    dataList() {
      this.axios
        .post(
          "/api/test",
          { name: "xiaoming", sex: "nan" },
          {
            headers: {
              "Content-Type": "application/x-www-form-urlencoded"
            }
          }
        )
        .then(function(res) {
          this.ruleForm = res.data.data;
          console.log(res.data);
          //控制台打印请求成功时返回的数据
        })
        .catch(function(err) {
          if (err.response) {
            console.log(err.response);
            //控制台打印错误返回的内容
          }
        });
    },
    resetForm() {}
  }
};
</script>




<style>
.el-form-item {
  margin-bottom: 2px;
}
</style>
