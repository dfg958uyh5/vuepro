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
      <div class="add">
        <ul class="tab-tilte">
          <li @click="cur=0" :class="{active:cur==0}">
             <input type="radio" :checked="0"></input>直线运动</li>
          <li @click="cur=1" :class="{active:cur==1}">
             <input type="radio" :checked="1" ></input>正弦运动</li>
              <el-button type="primary" class="ver" size="mini">ALL</el-button>
        </ul>

        <div class="tab-content">
          <div v-show="cur==0">
            <test1></test1>
          </div>

          <div v-show="cur==1">
            <test2></test2>
          </div>

        </div>

      </div>






    </el-form>
  </div>
</template>


<script>
import test1 from "./test1";
import test2 from "./test2";
export default {
  components: {
    test1,
     test2
  },
  data() {
    return {
       cur: 0, //默认选中第一个tab
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

.ver{
  margin-left:30px;
}

.tab-tilte li{
  font-size: 12px;
}
</style>

<style scoped>
ul li {
  margin: 0;
  padding: 0;
  list-style: none;
}
.add {
  width: 350px;
  height: 250px;
  margin: 0 auto;
  border: 1px solid #ccc;
}
.tab-tilte {
  width: 90%;
}
.tab-tilte li {
  float: left;
  width: 25%;
  padding: 10px 0;
  text-align: center;
  background-color: #f4f4f4;
  cursor: pointer;
}
/* 点击对应的标题添加对应的背景颜色 */
.tab-tilte .active {
  background-color: #09f;
  color: #fff;
}
.tab-content div {
  float: left;
  width: 90%;
  line-height: 20px;
  text-align: center;
}
</style>
