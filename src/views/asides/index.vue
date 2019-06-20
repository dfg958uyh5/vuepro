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
  }
};
</script>