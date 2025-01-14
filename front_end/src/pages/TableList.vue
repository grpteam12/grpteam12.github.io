<template>
  <div class="content">
    <div class="md-layout">
      <div
        class="md-layout-item md-medium-size-100 md-xsmall-size-100 md-size-100"
      >
        <md-card>
          <md-card-header data-background-color="green">
            <h4 class="title">Ranking Table</h4>
            <p class="category">Here is the table for the ranking files</p>
          </md-card-header>
          <md-card-content>
            <Ranking-table table-header-color="green"></Ranking-table>
          </md-card-content>
          <!-- 上传文件按钮 -->
          <md-button class="md-raised md-primary upload-button" @click="uploadFile">
              Upload Files
            </md-button>
            <input
              type="file"
              ref="fileInput"
              style="display: none"
              @change="handleFileUpload"
            />
        </md-card>
      </div>

      <div
        class="md-layout-item md-medium-size-100 md-xsmall-size-100 md-size-100"
      >
        <md-card class="md-card-plain">
          <md-card-header data-background-color="green">
            <h4 class="title">Ranked Table</h4>
            <p class="category">Here is a table for the ranked files</p>
          </md-card-header>
          <md-card-content>
            <Ranked-table></Ranked-table>
          </md-card-content>
        </md-card>
      </div>
    </div>
  </div>
</template>

<script>


import { RankingTable, RankedTable } from "@/components";

export default {
  components: {
    RankedTable,
    RankingTable,
  },

  methods: {
    // 打开文件选择框
    uploadFile() {
      this.$refs.fileInput.click();
    },
    // 处理文件上传
    handleFileUpload(event) {
      const file = event.target.files[0];
      if (file) {
        console.log("上传的文件：", file.name);
        // 在这里添加实际的文件上传逻辑
      }
    },
  },
};
</script>

<style scoped>
.upload-button {
  float: right;
  margin-top: 10px;
}
</style>
