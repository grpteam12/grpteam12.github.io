<template>
    <div class="content">
      <div class="md-layout">
        <div class="md-layout-item md-medium-size-100 md-xsmall-size-100 md-size-100">
          <md-card>
            <md-card-header data-background-color="green">
              <h4 class="title">Editable Table</h4>
              <p class="category">Fill in StudentID, SubjectID, and Marks</p>
            </md-card-header>
            <md-card-content>
              <table class="editable-table">
                <thead>
                  <tr>
                    <th>StudentID</th>
                    <th>SubjectID</th>
                    <th>Marks</th>
                    <th>Actions</th>
                  </tr>
                </thead>
                <tbody>
                  <tr v-for="(row, index) in tableData" :key="index">
                    <td><input v-model="row.StudentID" placeholder="Enter StudentID" /></td>
                    <td><input v-model="row.SubjectID" placeholder="Enter SubjectID" /></td>
                    <td><input v-model="row.Marks" placeholder="Enter Marks" type="number" /></td>
                    <td>
                      <button @click="removeRow(index)">Remove</button>
                    </td>
                  </tr>
                </tbody>
              </table>
              <button class="add-row-button" @click="addRow">Add Row</button>
              <button class="export-button" @click="exportTable('csv')">Export as CSV</button>
              <button class="export-button" @click="exportTable('txt')">Export as TXT</button>
            </md-card-content>
          </md-card>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        tableData: [
          { StudentID: "", SubjectID: "", Marks: "" } // 初始空白行
        ]
      };
    },
    methods: {
      addRow() {
        this.tableData.push({ StudentID: "", SubjectID: "", Marks: "" });
      },
      removeRow(index) {
        this.tableData.splice(index, 1);
      },
      exportTable(format) {
        let data = this.tableData;
        let content = "";
        
        // 将数据转换为 CSV 格式
        if (format === "csv") {
          content += "StudentID,SubjectID,Marks\n"; // 添加表头
          data.forEach(row => {
            content += `${row.StudentID},${row.SubjectID},${row.Marks}\n`;
          });
        }
        // 将数据转换为 TXT 格式
        else if (format === "txt") {
          content += "StudentID\tSubjectID\tMarks\n"; // 添加表头
          data.forEach(row => {
            content += `${row.StudentID}\t${row.SubjectID}\t${row.Marks}\n`;
          });
        }
        
        // 创建并下载文件
        const blob = new Blob([content], { type: "text/plain;charset=utf-8" });
        const link = document.createElement("a");
        link.href = URL.createObjectURL(blob);
        link.download = `table_data.${format}`;
        link.click();
        URL.revokeObjectURL(link.href);
      }
    }
  };
  </script>
  
  <style scoped>
  .editable-table {
    width: 100%;
    border-collapse: collapse;
  }
  .editable-table th, .editable-table td {
    border: 1px solid #ddd;
    padding: 8px;
  }
  .add-row-button, .export-button {
    margin-top: 10px;
    margin-right: 10px;
  }
  </style>
  