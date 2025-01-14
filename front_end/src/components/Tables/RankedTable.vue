<template>
  <div>
    <md-table v-model="RankedFiles" :table-header-color="tableHeaderColor">
      <md-table-row slot="md-table-row" slot-scope="{ item }">
        <md-table-cell md-label="ID">{{ item.id }}</md-table-cell>
        <md-table-cell md-label="Finshed Time">{{ item.FinshedTime }}</md-table-cell>
        <md-table-cell md-label="State">{{ item.State }}</md-table-cell>
        <!-- 此处应有超链接在ID上以供查看排序完成后的文件 -->
      </md-table-row>
    </md-table>
  </div>
</template>

<script>
export default {
  name: "ordered-table",
  props: {
    tableHeaderColor: {
      type: String,
      default: "",
    },
  },
  data() {
    return {
      selected: [],
      RankedFiles: [
        {
          id:"RankedFiles001",
          FinshedTime:"24/10/29/13:28",
          State:"Finsh Ranking"
        },
      ],
    };
  },
};
</script>
