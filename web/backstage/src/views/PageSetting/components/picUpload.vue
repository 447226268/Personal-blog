<template>
  <div id="picUpload">
    <el-upload
      action="https://jsonplaceholder.typicode.com/posts/"
      list-type="picture-card"
      multiple
      :on-preview="handlePictureCardPreview"
      :on-remove="handleRemove"
      :file-list="fileList"
    >
      <i class="el-icon-plus"></i>
    </el-upload>
    <el-dialog :visible.sync="dialogVisible">
      <img width="100%" :src="dialogImageUrl" alt="" />
    </el-dialog>
    <div class="button-display">
      <v-btn color="primary" elevation="2" width="100">保存</v-btn>
      <v-btn style="margin-left: 20px" color="primary" elevation="2" width="100"
        >发布</v-btn
      >
    </div>
  </div>
</template>

<script>
export default {
  name: 'picUpload',
  data: () => ({
    dialogImageUrl: '',
    dialogVisible: false,
    fileList: [
      {
        name: 'food.jpeg',
        url:
          'https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100'
      },
      {
        name: 'food2.jpeg',
        url:
          'https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100'
      }
    ]
  }),
  created () {
    setTimeout(() => {
      console.log(this.fileList)
    }, 1000)
  },
  methods: {
    handleRemove (file, fileList) {
      console.log(file, fileList)
    },
    handlePictureCardPreview (file) {
      this.dialogImageUrl = file.url
      this.dialogVisible = true
    }
  }
}
</script>

<style lang="scss" scoped>

#picUpload {
  ::v-deep.el-upload--picture-card {
    margin-bottom: 24px;
    &:hover {
      border-color: #4052b2;
    }
  }
  .button-display {
    text-align: right;
    margin-right: 3%;
  }
}
</style>
