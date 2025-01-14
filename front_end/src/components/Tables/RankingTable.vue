<template>
  <div>
    <md-table v-model="files" :table-header-color="tableHeaderColor">
      <md-table-row slot="md-table-row" slot-scope="{ item }">
        <md-table-cell md-label="ID">{{ item.ID }}</md-table-cell>
        <md-table-cell md-label="Uploaded Time">{{ item.UploadedTime }}</md-table-cell>
        <md-table-cell md-label="State">{{ item.State }}</md-table-cell>
        <md-table-cell md-label="The order">{{ item.TheOrder }}</md-table-cell>
        <!-- 此处应有超链接在ID上以供查看上传的文件 -->
      </md-table-row>
    </md-table>
  </div>
</template> 

<script>
export default {
  name: "simple-table",
  props: {
    tableHeaderColor: {
      type: String,
      default: "",
    },
  },
  data() {
    return {
      selected: [],
      files: [
        {
          ID: "files001",
          UploadedTime: "10/28/10:28",
          State: "Waiting",
          TheOrder: "01",
        },
      ],
    };
  },
};
</script>
