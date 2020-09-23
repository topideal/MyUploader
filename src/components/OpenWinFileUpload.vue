<!-- 一个上传事例文件 -->
<template>
  <div>
    <el-button @click="upload">上传</el-button>
    <global-uploader/>
  </div>
</template>

<script>
  import Bus from '@/assets/js/bus';
  import GlobalUploader from '@/components/GlobalUploader'

  export default {
    name: "OpenWinFileUpload",
    components: {
      GlobalUploader
    },
    data() {
      return {}
    },
    mounted() {
      // 文件选择后的回调
      Bus.$on('fileAdded', () => {
        console.log('文件已选择')
      });

      // 文件上传成功的回调
      Bus.$on('fileSuccess', (v) => {
        console.log('文件上传成功',v)
      });
    },
    computed: {},
    methods: {
      upload() {
        // 打开文件选择框
        Bus.$emit('openUploader', {
          userUid: 'chen'  // 传入的参数
        })
      }
    },
    destroyed() {
      Bus.$off('fileAdded');
      Bus.$off('fileSuccess');
    },
  }
</script>


