<template>
  <div>
    <el-tree
      :data="data2"
      show-checkbox
      node-key="id"
      :default-expanded-keys="[2, 3]"
      :default-checked-keys="[5]"
      :props="defaultProps"
    ></el-tree>
  </div>
</template>

<script>
export default {
  data() {
    return {
      data: [],
      data2: [
        {
          id: 1,
          label: "一级 1",
          children: [
            {
              id: 4,
              label: "二级 1-1",
              children: [
                {
                  id: 9,
                  label: "三级 1-1-1"
                },
                {
                  id: 10,
                  label: "三级 1-1-2"
                },
                {
                  id: 11,
                  label: "三级 1-1-3"
                }
              ]
            }
          ]
        },
        {
          id: 2,
          label: "一级 2",
          children: [
            {
              id: 4,
              label: "二级 2-1",
              children: [
                {
                  id: 9,
                  label: "三级 2-1-1"
                },
                {
                  id: 10,
                  label: "三级 2-1-2"
                },
                {
                  id: 11,
                  label: "三级 2-1-3"
                }
              ]
            }
          ]
        },
        {
          id: 3,
          label: "一级 3",
          children: [
            {
              id: 4,
              label: "二级 3-1",
              children: [
                {
                  id: 9,
                  label: "三级 3-1-1"
                },
                {
                  id: 10,
                  label: "三级 3-1-2"
                },
                {
                  id: 11,
                  label: "三级 3-1-3"
                }
              ]
            }
          ]
        }
      ],
      defaultProps: {
        children: "children",
        label: "label"
      }
    };
  },
  methods: {
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
          //   this.ruleForm = res.data.data;
          this.data = res.data.data;
          console.log(res.data);
          //控制台打印请求成功时返回的数据
        })
        .catch(function(err) {
          if (err.response) {
            console.log(err.response);
            //控制台打印错误返回的内容
          }
        });
    }
  }
};
</script>