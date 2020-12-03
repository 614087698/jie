<template>
  <div class="about">
    <h1>This is an about page</h1>
    <el-input v-model="input2" placeholder="请输入内容"></el-input>
  </div>
</template>

<script>
export default {
  data() {
    return {
      input2: '',
    }
  }
}
