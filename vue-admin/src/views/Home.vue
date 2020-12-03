<template>
  <div class="home">
    <el-form ref="form" :model="form" label-width="100px">
      <el-form-item label="时间筛选：">
        <el-date-picker
          v-model="value1"
          type="daterange"
          range-separator="至"
          start-placeholder="开始日期"
          end-placeholder="结束日期"
        >
        </el-date-picker>
        <div class="w10"></div>
        <el-button type="primary">查询</el-button>
        <el-button type="primary">导出Excel</el-button>
      </el-form-item>

      <el-table border :data="tableData" style="width: 100%">
        <el-table-column
          prop="Number"
          label="序号"
          width="180"
        ></el-table-column>
        <el-table-column
          prop="Phone"
          label="电话"
          width="180"
        ></el-table-column>
        <el-table-column prop="Wechat" label="微信号"> </el-table-column>
        <el-table-column prop="Region" label="所属地区"> </el-table-column>
        <el-table-column prop="IP" label="IP"> </el-table-column>
        <el-table-column prop="Time" label="访问时间"> </el-table-column>
        <el-table-column prop="Url" label="URL"> </el-table-column>
      </el-table>
      <!-- <el-pagination background layout="prev, pager, next" :total="1000">
      </el-pagination> -->
    </el-form>
  </div>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      value1: "",
      tableData: [
        {
          Number: "",
          Phone: "",
          Wechat: "",
          Region: "",
          IP: "",
          Time: "",
          Url: "",
        },
      ],
    };
  },
  methods: {},
};
</script>

<style lang="less">
.w10 {
  display: inline-block;
  width: 10px;
}
</style>
