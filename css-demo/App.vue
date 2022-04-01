<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style lang="less">
	/*每个页面公共css */
	@import url("@/common/iconfont.css");
	@import url("@/common/animate.css");
	@import url("@/common/index.less");

	.AppColors( {
			/* 品牌色 */
			primary: #570df8;
			/* 主要 */
			secondary: #f000b8;
			/* 次要 */
			accent: #37cdbe;
			/* 强调 */
			neutral: #3d4451;
			/* 中和 */
			base: #7f899a;
			/* 基础 */

			/* 通用色 */
			info: #3b82f6;
			/* 信息 */
			success: #10b981;
			/* 成功 */
			warning: #f59e0b;
			/* 警告 */
			error: #ef4444;
			/* 错误 */

			/* 点击时，品牌色 */
			primary-focus: #4406cb;
			/* 主要 */
			secondary-focus: #bd0091;
			/* 次要 */
			accent-focus: #2aa79b;
			/* 强调 */
			neutral-focus: #2a2e37;
			/* 中和 */
			base-focus: #656f7f;
			/* 基础 */

			/* 点击时，通用色 */
			info-focus: #2563eb;
			/* 信息 */
			success-focus: #059669;
			/* 成功 */
			warning-focus: #d97706;
			/* 警告 */
			error-focus: #dc2626;
			/* 错误 */

			/* 白色 */
			white: #ffffff;
		}

	);
</style>
