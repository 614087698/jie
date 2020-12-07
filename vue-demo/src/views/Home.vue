<template>
  <div class="home">
    <el-form ref="form" :model="form" label-width="100px">
      <el-form-item label="时间筛选：">
        <el-date-picker
          v-model="form.value"
          format="yyyy-MM-dd" 
          value-format="yyyy-MM-dd"
          type="daterange"
          range-separator="至"
          start-placeholder="开始日期"
          end-placeholder="结束日期"
          @change="selectTime"
        >
        </el-date-picker>
        <div class="w10"></div>
        <el-button type="primary" @click="query()">查询</el-button>
        <el-button type="primary" @click="leadingOut()">导出Excel</el-button>
      </el-form-item>

      <el-table border :data="tableData" style="width: 100%">
        <!-- <el-table-column
          prop="id"
          label="序号"
          width="80"
        ></el-table-column> -->
        <el-table-column
          prop="dMobile"
          label="电话"
          width="180"
        ></el-table-column>
        <el-table-column prop="dWechatNo" label="微信号"> </el-table-column>
        <el-table-column prop="Region" label="所属地区"> </el-table-column>
        <el-table-column prop="dIp" label="IP"> </el-table-column>
        <el-table-column prop="createTime" label="访问时间"> </el-table-column>
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
      form: {
        value: "",
      },
      tableData: [
        {
          Number: "",
          Phone: "",
          Wechat: "",
          Region: "",
          dIp: "",
          createTime: "",
          Url: "",
        },
      ],
    };
  },

  methods: {
    list() {
      this.$axios
        .post("https://server.shenxiaoqiang.vip/zhuzhong/info/list", {
          page: 1,
          rows: 100,
        })
        .then((res) => {
          console.log(res.data.data.rows);
          this.tableData = res.data.data.rows;
        })
        .catch((err) => {
          console.log(err);
        });
    },

    selectTime(val){
      this.form.value1 = val
      // console.log(val)
    },
    
    query() {
      this.$axios
        .post("https://server.shenxiaoqiang.vip/zhuzhong/info/list", {
          page: 1,
          rows: 100,
          startDate: this.form.value[0],
          endDate: this.form.value[1],
        })
        .then((res) => {
          console.log(res.data.data.rows);
          this.tableData = res.data.data.rows;
        })
        .catch((err) => {
          console.log(err);
        });
    },
    leadingOut() {
      this.$axios
        .post("https://server.shenxiaoqiang.vip/zhuzhong/info/export", {
          startDate: this.form.value[0],
          endDate: this.form.value[1],
        })
        .then((res) => {
          console.log(res.data.data.rows);
          // this.tableData = res.data.data.rows;
        })
        .catch((err) => {
          console.log(err);
        });
    },

  },
  created() {
    this.list();
  },
};
</script>

<style lang="less">
.w10 {
  display: inline-block;
  width: 10px;
}
</style>
