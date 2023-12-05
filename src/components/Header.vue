<template>
	<div>

	</div>
</template>

<script>
const OK = 200
export default {
  data () {
    return {
      activeIndex: '1',
      adminAccessUrl: 'http://118.89.228.250:8012'
    }
  },
  methods: {
    getAdminUrl: function () {
      this.$axios.get('/api/system/adminUrl').then(res => {
        if (res.data.code == OK) {
          this.adminAccessUrl = res.data.data
        }
      })
    },
    goAdminUrl: function () {
      // window.location.href = this.adminAccessUrl
      window.open(this.adminAccessUrl, '_blank')
    }
  },
  created: function () {
    // this.getAdminUrl()
  },
  mounted: function () {}
}
</script>

<style scoped="scoped">
.header-wrap {
	background-color: #9a0e14;
  position: fixed;
  left: 0;
  right: 0;
  top:0;
  height: 70px;
}
.phone-nav {
		display: none;
	}
.header {
	width: 1024px;
	height: 70px;
	line-height: 70px;
	margin: 0 auto;
}

.el-menu.el-menu--horizontal a {
	color: #fff;
}
.rightMenu {
	float: right;
	height: 70px;
	line-height: 70px;
	background-color: #000000;
}
a {
	text-decoration: none;
	color: #eee;
	font-size: 16px;
}
/* @media screen and (min-width: 1196px) {
	.phone-nav {
		display: none;
	}
} */
/* @media screen and (max-width: 600px) {
	.computerNav {
		display: none;
	}
	.phone-nav {
		display: block;
	}
} */
</style>
