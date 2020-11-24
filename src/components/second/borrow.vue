<template>
  <div>
    <div class="top">
      <el-button type="primary" @click="create">添加</el-button>
    </div>
    <div class="block">
      <el-table :data="messageList">
        <el-table-column type="selection" width="55"></el-table-column>
        <el-table-column prop="number" label="图书编号"></el-table-column>
        <el-table-column prop="name" label="书名"></el-table-column>
        <el-table-column prop="borrowDate" label="借书时间"></el-table-column>
        <el-table-column prop="backDate" label="归还时间"></el-table-column>
        <el-table-column prop="readerId" label="读者ID"></el-table-column>
      </el-table>
      <el-pagination
        @size-change="handleSizeChange"
        @current-change="handleCurrentChange"
        :current-page="currentPage4"
        :page-size="5"
        layout="total, prev, pager, next, jumper"
        :total="count"
      ></el-pagination>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    create() {
      this.$router.push("/creatBorrow")
    }
  }
}
</script>

<style>

</style>