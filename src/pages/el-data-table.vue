<template>
  <!-- <el-data-table></el-data-table> -->
  <div class="table">
    <el-data-table v-bind="tableConfig"></el-data-table>
  </div>
</template>
<script>
import ElDataTable from 'el-data-table'
export default {
  layout: 'el-data-table',
  components: {
    'el-data-table': ElDataTable
  },
  data() {
    return {
      tableConfig: {
        url: '/api/v1/users',
        firstPage: 1,
        columns: [
          {type: 'selection'},
          {prop: 'name', label: '组件名称'},
          {prop: 'class', label: '分类'},
          {prop: 'version', label: '版本'},
          {prop: 'lang', label: '开发语言'},
          {prop: 'time', label: '最后更新时间'},
          {prop: 'status', label: '状态'}
        ],
        searchForm: [
          {
            $type: 'input',
            $id: 'name',
            label: '组件名称',
            $el: {
              placeholder: '请输入'
            }
          },
          {
            $type: 'select',
            $id: 'name',
            label: '分类',
            $el: {
              placeholder: '请输入'
            },
            $options: [
              {
                label: '区域一',
                value: 'shanghai'
              },
              {
                label: '区域二',
                value: 'beijing'
              }
            ]
          },
          {
            $type: 'select',
            $id: 'name',
            label: '状态',
            $el: {
              placeholder: '请输入'
            },
            $options: [
              {
                label: '区域一',
                value: 'shanghai'
              },
              {
                label: '区域二',
                value: 'beijing'
              }
            ]
          }
        ],
        form: [
          {
            $type: 'input',
            $id: 'name',
            label: '状态',
            $el: {
              placeholder: '请输入'
            },
            rules: [
              {
                required: true,
                message: '请输入用户名',
                trigger: 'blur'
              }
            ]
          }
        ],
        extraButtons: [
          {
            type: 'text',
            text: '查询',
            atClick(row) {
              alert(row.name)
            }
          },
          {
            type: 'text',
            text: '编辑',
            atClick(row) {
              alert(row.name)
            }
          },
          {
            type: 'text',
            text: '下架',
            atClick(row) {
              alert(row.name)
            }
          }
        ],
        tableAttrs: {
          'cell-style': function({row, column, rowIndex, columnIndex}) {
            if (row.status == '上架' && columnIndex == 6) {
              return {
                color: 'lightgreen'
              }
            }
            return {
              color: ''
            }
          }
        }
      }
    }
  },
  created() {
    console.log(666)
    // this.$axios.get('https://api.github.com/search/users?q=FEMessage&size=10&page=1').then(res => {
    //   console.log(res);

    // })
  },
  methods: {
    onDelete() {
      console.log(1)
    }
  }
}
</script>
<style lang="less" scoped>
.table {
  padding: 20px;
}
</style>
