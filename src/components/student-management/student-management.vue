<template>
<div>
    <el-table
      :data="tableData"
      style="width: 100%">
      <el-table-column
        prop="date"
        label="日期"
        width="250">
      </el-table-column>
      <el-table-column
        prop="name"
        label="姓名"
        width="250">
      </el-table-column>
      <el-table-column
        prop="address"
        label="地址"
        width="500">
    </el-table-column>
    <el-table-column label="操作">
        <template slot-scope="scope">
        <el-button
          size="mini"
          @click="handleEdit(scope.$index, scope.row)">编辑</el-button>
        <el-button
          size="mini"
          type="danger"
          @click="handleDelete(scope.$index, scope.row)">删除</el-button>
      </template>
    </el-table-column>
  </el-table>
  <!-- 给子组件传值 dialogVisible -->
  <edit-modal :dialogVisible="dialogVisible" @cancelModal="cancelModal"></edit-modal>
  </div>
</template>
<script>

import editModal from './edit-modal.vue';
export default {
components: { editModal },
    name: 'StudentManagement',
    data() {
        return {
            dialogVisible: false,
            tableData: [{
            date: '2016-05-02',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1518 弄',
            }, {
            date: '2016-05-04',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1517 弄'
            }, {
            date: '2016-05-01',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1519 弄'
            }, {
            date: '2016-05-03',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1516 弄'
            }]
        }
    },

    methods: {
        handleEdit(index, row) {
            console.log(index, row);
            this.dialogVisible = true
        },
        handleDelete(index, row) {
            console.log(index, row);
        },
        // 关闭modal
        cancelModal() {
            this.dialogVisible = false;
        },
    }
}
</script>