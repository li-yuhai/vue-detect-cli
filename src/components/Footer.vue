<template>
	<div class="footer-wrap">
		<div class="footer">
			<p class="introduce">欢迎2023年12月4日部署遂宁和pest24融合模型害虫检测</p>
			<p>Copyright RF All rights reserved.</p>
		</div>
	</div>
</template>

<script>
export default {

}
</script>

<style scoped="scoped">
	.footer-wrap {
		/*background-color:#9a0e14 ;*/
    background-color: #ffffff;
    position: fixed;
    left: 0;
    right: 0;
    bottom:0;
    height: 70px;
	}

	.footer-wrap .footer {
		width: 1024px;
		margin: 0 auto;
		height: 70px;
	}
  .introduce{
    margin: 10px;
  }
	.footer-wrap .footer p{
		line-height: 16px;
	}

	@media screen and (max-width: 600px){
	  .footer-wrap {
	  	padding: 2px 15px;
	  }
	}
</style>
