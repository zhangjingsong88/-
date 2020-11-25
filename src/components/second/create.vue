<template>
  <div id="box">
      <el-form ref="form" :model="form" label-width="80px">
      <el-form-item label="图书编号">
        <el-input v-model="form.id" style="width: 40%;"></el-input>
      </el-form-item>
      <el-form-item label="书名">
        <el-input v-model="form.bookname" style="width: 40%;"></el-input>
      </el-form-item>
      <el-form-item label="作者">
        <el-input v-model="form.auther" style="width: 40%;"></el-input>
      </el-form-item>
      <el-form-item label="类型">
        <el-input v-model="form.type" style="width: 40%;"></el-input>
      </el-form-item>
      <el-form-item label="出版商">
        <el-input v-model="form.publisher" style="width: 40%;"></el-input>
      </el-form-item>
      <el-form-item label="库存">
        <el-input v-model="form.stock" style="width: 40%;"></el-input>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="onSubmit">立即创建</el-button>
        <el-button @click="getBack">取消</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>
<script>
export default {
  data() {
    return {
      isShow: false,
      fileList: "",
      form: {
        bookname: "夏洛的网",
        auther: "EB怀特",
        type: "文学作品",
        publisher: "凤凰出版社",
        stock: "4812",
        id: "FB154"
      }
    };
  },
  methods: {
    onSubmit() {
      this.$http({
        url: "/book/add_book",
        params: {
          bookname: this.form.bookname,
          auther: this.form.auther,
          id: this.form.id,
          type: this.form.type,
          publisher: this.form.publisher,
          stock: this.form.stock 
        }
      })
        .then(res => {
          console.log(res, "res");
          // if (res.data.code == 0) {
          //   this.$message({
          //     message: res.data.info,
          //     type: "success"
          //   });
            this.$router.push("/index");
          // } else {
          //   this.$message({
          //     message: res.data.info,
          //     type: "error"
          //   });
          // }
        })
        .catch(err => {});
    },
    //返回上一层
    getBack() {
      this.$router.go(-1);
    }
  }
};
</script>
<style lang="" scoped>
#box {
  flex: 1;
}
</style>