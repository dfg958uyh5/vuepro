<template>
  <div>
    <el-form
      :model="ruleForm"
      :rules="rules"
      ref="ruleForm"
      label-width="100px"
      class="demo-ruleForm"
    >
      <el-row>
        <el-col :span="6">
          <el-form-item label="通道号选择" prop="name">
            <el-input-number
              v-model="num8"
              controls-position="right"
              @change="handleChange"
              :min="1"
              :max="10"
            ></el-input-number>
          </el-form-item>
        </el-col>
        <el-col :span="6">
          <el-form-item>
            <el-button type="primary" @click="onSubmit">仿真起始时间</el-button>
          </el-form-item>
        </el-col>
        <el-col :span="6">
          <el-form-item>
            <el-button type="primary" @click="onSubmit">广播信息设置</el-button>
          </el-form-item>
        </el-col>
      </el-row>

      <el-row>
        <el-col :span="6">
          <el-form-item label="分帧号选择" prop="name">
            <el-input-number v-model="num1" @change="handleChange" :min="1" :max="10" label="描述文字"></el-input-number>
          </el-form-item>
        </el-col>
        <el-col :span="6">
          <el-form-item>
            <el-button type="primary" @click="onSubmit">帧度模块设置</el-button>
          </el-form-item>
        </el-col>
      </el-row>
      <el-row>
        <P>I支路</P>
        <el-col :span="6">
          <el-form-item label="公用" prop="name">
            <el-input v-model="ruleForm.name"></el-input>
          </el-form-item>
        </el-col>
        <el-col :span="7">
          <el-form-item label="抑制" prop="region">
            <el-select v-model="ruleForm.region" placeholder="请选择活动区域">
              <el-option label="区域一" value="shanghai"></el-option>
              <el-option label="区域二" value="beijing"></el-option>
            </el-select>
          </el-form-item>
        </el-col>
        <el-col :span="6">
          <el-form-item label="I支路" prop="name">
            <el-input v-model="ruleForm.name"></el-input>
          </el-form-item>
        </el-col>
      </el-row>
      <!--  -->
      <!-- <el-row>
        <el-col :span="6">
          <el-form-item label prop="resource">
            <el-radio-group v-model="ruleForm.resource">
              <el-row>
                <el-radio label="定位信息"></el-radio>
              </el-row>
              <el-row>
                <el-radio label="通信信息"></el-radio>
              </el-row>
              <el-row>
                <el-radio label="通信回执"></el-radio>
              </el-row>
              <el-row>
                <el-radio label="其他信息"></el-radio>
              </el-row>
              <el-row>
                <el-radio label="空帧"></el-radio>
              </el-row>
            </el-radio-group>
          </el-form-item>
      </el-col>-->
      <!--  -->
      <!-- <el-col :span="18"> -->
      <!--lalalala  -->
      <!-- <el-row>
            <el-col :span="7">
              <el-form-item label="通信形式" prop="region">
                <el-select v-model="ruleForm.region" placeholder="请选择活动区域">
                  <el-option label="区域一" value="shanghai"></el-option>
                  <el-option label="区域二" value="beijing"></el-option>
                </el-select>
              </el-form-item>
            </el-col>
            <el-col :span="6">
              <el-form-item label="收信方地址" prop="name">
                <el-input v-model="ruleForm.name"></el-input>
              </el-form-item>
            </el-col>
          </el-row>
          <el-row>
            <el-form-item label="回执数" prop="region">
              <el-select v-model="ruleForm.region" placeholder="请选择活动区域">
                <el-option label="区域一" value="shanghai"></el-option>
                <el-option label="区域二" value="beijing"></el-option>
              </el-select>
            </el-form-item>
      </el-row>-->
      <!-- 空白框 -->
      <!-- <el-form-item prop="desc">
            <el-input type="textarea" v-model="ruleForm.desc"></el-input>
      </el-form-item>-->
      <!-- 四个input框 -->
      <!-- <el-row>
            <el-col :span="6">
              <el-form-item label="发出时间" prop="name">
                <el-input v-model="ruleForm.name"></el-input>
              </el-form-item>
            </el-col>
            <el-col :span="6">
              <el-form-item label="h" prop="name">
                <el-input v-model="ruleForm.name"></el-input>
              </el-form-item>
            </el-col>
          </el-row>
          <el-row>
            <el-col :span="6">
              <el-form-item label="回执时间" prop="name">
                <el-input v-model="ruleForm.name"></el-input>
              </el-form-item>
            </el-col>
            <el-col :span="6">
              <el-form-item label="h" prop="name">
                <el-input v-model="ruleForm.name"></el-input>
              </el-form-item>
            </el-col>
      </el-row>-->
      <!-- lalalala -->
      <!-- </el-col>
      </el-row>-->
      <!--   -->

      <el-tabs type="border-card" tab-position="left">
        <el-tab-pane>
          <span slot="label">
            <el-radio v-model="radio" label="1">定位信息</el-radio>
          </span>
          <test1></test1>
        </el-tab-pane>
        <el-tab-pane>
          <span slot="label">
            <el-radio v-model="radio" label="2">通信信息</el-radio>
          </span>
          <test2></test2>
        </el-tab-pane>
        <el-tab-pane>
          <span slot="label">
            <el-radio v-model="radio" label="3">通信回执</el-radio>
          </span>
          <test3></test3>
        </el-tab-pane>
        <el-tab-pane>
          <span slot="label">
            <el-radio v-model="radio" label="4">其他信息</el-radio>
          </span>
          定时任务补偿
        </el-tab-pane>
        <el-tab-pane>
          <span slot="label">
            <el-radio v-model="radio" label="5">空帧</el-radio>
          </span>
          定时任务补偿
        </el-tab-pane>
      </el-tabs>
    </el-form>
  </div>
</template>







<script>
import test3 from "./test3";
import test2 from "./test2";
import test1 from "./test1";
export default {
  components: {
    test3,
    test2,
    test1
  },
  data() {
    return {
      radio: "1", //tab切换
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







<style>
.tab-tilte li {
  font-size: 12px;
}
</style>



