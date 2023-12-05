<template>
	<div>
    <div>
      <el-upload
        class="upload-demo"
        drag
        action="#"
        :http-request="HttpRequest"
        multiple>
        <i class="el-icon-upload"></i>
        <div class="el-upload__text">将文件拖到此处，或<em>点击上传</em></div>
        <div class="el-upload__tip" slot="tip">只能上传jpg文件，且不超过500kb</div>
      </el-upload>
    </div>

    <div class="det_res">
      <div class="demo-image__placeholder">
        <div class="block" >
          <span class="demonstration">检测效果图</span>
          <el-image :src="det_img">
            <div slot="error" class="image-slot">
              <i class="el-icon-picture-outline"></i>
            </div>
          </el-image>
        </div>
        <div class="block">
          <span class="demonstration">原图</span>
          <el-image :src="det_origin_img">
            <div slot="placeholder" class="image-slot">
              加载中<span class="dot">...</span>
            </div>
            <div slot="error" class="image-slot">
              <i class="el-icon-picture-outline"></i>
            </div>
          </el-image>
        </div>
      </div>
    </div>
	</div>
</template>

<script>
export default {
  data () {
    return {
      post_img_url: '',
      det_img: '',
      det_origin_img: '',
      det_json: '',
      pic_static_url: 'http://127.0.0.1:8888/static/'
    }
  },
  methods: {
    HttpRequest:function (data){
      // new 一个formdata 对象 将我们的参数和文件赋值进去
      const formdata = new FormData()
      formdata.append('file', data.file)
      // formdata.append('type', 'img')
      // console.log(data.file)
      // post请求后端接口，注意跨域请求
      this.$axios.post(process.env.API_HOST + '/detect', formdata).then(res => {
        if(res.status == 200){
            data = res.data
            this.det_img = this.pic_static_url+  data.det_img_path
            this.det_json = data.result
            this.det_origin_img = this.pic_static_url + data.det_origin_img
            // console.log(data)
            // console.log(this.det_img)
            // console.log(this.det_origin_img)
        }else{
          this.$message.error("服务出现错误,联系管理员:17623139140")
        }
      })
      // this.$axios({
      //   method: "post",
      //   url: "/api/detect",
      //   data: {
      //     file: data.file
      //   }
      // }).then(result => {
      //     console.log(result)
      // })
    },
    // post_img: function(event, file, fileList){
    //    console.log(file)
    // },
    // post_img_success: function(response, file, fileList) {
    //    console.log(response)
    // }
  },
  created: function () {

  },
  mounted: function () {}
}
</script>

<style scoped="scoped">
.det_res{
  margin-top: 200px;
}

</style>
