<template>
  <vue-virtual-table
    :config="tableConfig"
    :data="tableData"
    :height="800"
    :itemHeight="55"
    :minWidth="1000"
    :selectable="true"
    :enableExport="true"
    :language='en'
    v-on:changeSelection="handleSelectionChange"
  >
    <template slot-scope="scope" slot="actionCommon">
      <button @click="edit(scope.index, scope.row)">Edit</button>
      <button @click="del(scope.index, scope.row)">Delete</button>
    </template>
  </vue-virtual-table>
</template>

<script>
  import VueVirtualTable from 'vue-virtual-table'
  export default {
    components: {
      VueVirtualTable
    },
    data() {
      return {
        tableConfig: [
          {prop: '_index', name: '#', width: 80},
          {prop: 'user', name: 'User', searchable: true, sortable: true, summary: 'COUNT'},
          {prop: 'age', name: 'Age', numberFilter: true},
          {prop: 'city', name: 'City', filterable: true},
          {prop: '_action', name: 'Action', actionName: 'actionCommon'}
        ],
        tableData: [
          {user: '무지', age: 20, city: '포항'},
          {user: '케니', age: 21, city: '서울'},
          {user: '토니', age: 23, city: '미국'},
          {user: '네오', age: 23, city: '미국'},
          {user: '샌디', age: 23, city: '미국'}
        ]
      };
    },
    methods: {
      handleSelectionChange(rows){
        console.info(rows  )
      },
      edit(index, row){
        console.info(index)
      },
      del(index, row){
        console.info(index)
      }
    }
  }
</script>
