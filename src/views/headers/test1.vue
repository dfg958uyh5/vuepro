<template>
  <div>
    <p>信息类别</p>
    <el-row>
      <el-col :span="8">
        <el-form-item label="通信形式" prop="region">
          <el-select v-model="ruleForm.region" placeholder="请选择活动区域">
            <el-option label="区域一" value="shanghai"></el-option>
            <el-option label="区域二" value="beijing"></el-option>
          </el-select>
        </el-form-item>
      </el-col>
      <el-col :span="8">
        <el-form-item label="电文形式" prop="region">
          <el-select v-model="ruleForm.region" placeholder="请选择活动区域">
            <el-option label="区域一" value="shanghai"></el-option>
            <el-option label="区域二" value="beijing"></el-option>
          </el-select>
        </el-form-item>
      </el-col>
      <el-col :span="8">
        <el-form-item label="电文形式" prop="region">
          <el-select v-model="ruleForm.region" placeholder="请选择活动区域">
            <el-option label="区域一" value="shanghai"></el-option>
            <el-option label="区域二" value="beijing"></el-option>
          </el-select>
        </el-form-item>
      </el-col>
    </el-row>
    <el-row>
      <el-col :span="6">
        <el-form-item prop="type">
          <el-checkbox-group v-model="ruleForm.type">
            <el-checkbox label="有密钥" name="type"></el-checkbox>
          </el-checkbox-group>
        </el-form-item>
      </el-col>
      <el-col :span="6">
        <el-form-item prop="type">
          <el-checkbox-group v-model="ruleForm.type">
            <el-checkbox label="有密钥" name="type"></el-checkbox>
          </el-checkbox-group>
        </el-form-item>
      </el-col>
      <el-col :span="6">
        <el-form-item prop="type">
          <el-checkbox-group v-model="ruleForm.type">
            <el-checkbox label="有密钥" name="type"></el-checkbox>
          </el-checkbox-group>
        </el-form-item>
      </el-col>
    </el-row>
    <p>高程数据</p>
     <el-row>
      <el-col :span="7">
        <el-form-item label="发信方地址" prop="name">
          <el-input v-model="ruleForm.name"></el-input>
        </el-form-item>
      </el-col>
      <el-col :span="4">
        <el-form-item label="发" prop="name">
          <el-input v-model="ruleForm.name"></el-input>
        </el-form-item>
      </el-col>
      <el-col :span="4">
        <el-form-item label="h" prop="name">
          <el-input v-model="ruleForm.name"></el-input>
        </el-form-item>
      </el-col>
       <el-col :span="4">
        <el-form-item label="发" prop="name">
          <el-input v-model="ruleForm.name"></el-input>
        </el-form-item>
      </el-col>
      <el-col :span="4">
        <el-form-item label="h" prop="name">
          <el-input v-model="ruleForm.name"></el-input>
        </el-form-item>
      </el-col>
    </el-row>
    <el-row>
      <el-col :span="7">
        <el-form-item label="发信方地址" prop="name">
          <el-input v-model="ruleForm.name"></el-input>
        </el-form-item>
      </el-col>
      <el-col :span="4">
        <el-form-item label="发" prop="name">
          <el-input v-model="ruleForm.name"></el-input>
        </el-form-item>
      </el-col>
      <el-col :span="4">
        <el-form-item label="h" prop="name">
          <el-input v-model="ruleForm.name"></el-input>
        </el-form-item>
      </el-col>
       <el-col :span="4">
        <el-form-item label="发" prop="name">
          <el-input v-model="ruleForm.name"></el-input>
        </el-form-item>
      </el-col>
      <el-col :span="4">
        <el-form-item label="h" prop="name">
          <el-input v-model="ruleForm.name"></el-input>
        </el-form-item>
      </el-col>
    </el-row>
    

  </div>
</template>








<script>
export default {
  data() {
    return {
      num8: 1,
      num1: 1,
      ruleForm: {
        name: "",
        region: "",
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
        region: [
          { required: true, message: "请选择活动区域", trigger: "change" }
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
    dataList() {
      this.axios
        .post(
          "/api/v1/device/{deviceId}/SwitchButton",
          { name: "Switch" },
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