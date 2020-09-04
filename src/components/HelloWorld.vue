<template>
  <div class="hello">
    <br><br>
    <el-button type="primary" @click="getRequest">Get测试</el-button>
      <el-table
        :data="role"
        border
        style="width: 1200px; margin-top: 20px;">
        <el-table-column label="id" width="400px">
          <template slot-scope="scope">
            <span>{{ scope.row.id }}</span>
          </template>
        </el-table-column>
        <el-table-column label="角色" width="400px">
          <template slot-scope="scope">
            <span>{{ scope.row.roleName }}</span>
          </template>
        </el-table-column>
        <el-table-column label="描述" width="400px">
          <template slot-scope="scope">
            <span>{{ scope.row.note }}</span>
          </template>
        </el-table-column>
      </el-table>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Vue前端Demo',
      role: null,
      code: null
    }
  },
  created () {
  },
  methods: {
    getRequest () {
      this.$axios.get('/role/getByName1', {

      }).then(res => {
        this.code = res.data.code
        this.role = res.data.data
        console.log(res)
      })
    }
  }
}
</script>
