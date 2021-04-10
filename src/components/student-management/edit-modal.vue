<template>
    <el-dialog
    title="提示"
    :visible="dialogVisible"
    width="30%"
    :before-close="handleClose">
    <span>这是一段信息</span>
    <span slot="footer" class="dialog-footer">
        <el-button @click="cancelModal">取 消</el-button>
        <el-button type="primary" @click="cancelModal">确 定</el-button>
    </span>
    </el-dialog>
</template>

<script>
  export default {
    // props接收父组件传过来的值
    props: [
        'dialogVisible'
    ],
    data() {
      return {
        // dialogVisible: this.dialogVisible
      };
    },
    methods: {
      cancelModal(){
          // 通知父类关闭modal
          this.$emit('cancelModal');
      },  
      handleClose(done) {
        this.$confirm('确认关闭？')
          .then(_ => {
            done();
          })
          .catch(_ => {});
      }
    }
  };
</script>