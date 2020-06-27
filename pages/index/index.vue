<template>
	<view class="">
		<!-- 滑动栏 -->
		<view class="">
			<scroll-view
				class="scroll-container"
				scroll-x="true"
				scroll-with-animation
				v-if="brands.length > 1"
				:scroll-into-view="'s' + currentIndex"
			>
				<view
					:class="['scroll-item', { active: index == currentId }]"
					:id="'s' + index"
					v-for="(item, index) in brands"
					:key="index"
					@click="handleScroll(index)"
				>
					<view>{{ item }}</view>
				</view>
			</scroll-view>
		</view>
		<!-- 滑动栏 -->
		<!-- 拼小圈 -->
		<view class="flex-row invite">
			<view class="invite-left">
				<image src="../../static/home-icon/round-icon.png" mode=""></image>
				<text>拼小圈</text>
			</view>

			<view class="flex-row invite-right">
				<view class="invite-right-img">
					<image src="../../static/home-icon/person-img1.png" mode=""></image>
					<image src="../../static/home-icon/person-img2.png" mode=""></image>
					<image src="../../static/home-icon/person-img3.png" mode=""></image>
				</view>
				<view>邀请您开启</view>
				<view class="right"></view>
			</view>
		</view>
		<!-- 拼小圈 -->
		<view class="tab-navigation">
			<swiper class="navigation-swiper" indicator-dots="true" autoplay="false" circular="true" display-multiple-items="5">
				<swiper-item class="navigation-swiper-item">
					<view class="swiper-item-top" >
						<image src="../../static/navigation-icon/icon-piggy.png"></image>
						<text>限时秒杀</text>
					</view>
					<view class="swiper-item-bottom" >
						<image src="../../static/navigation-icon/icon-bargain.png"></image>
						<text>9.9价多卖</text>
					</view>
				</swiper-item>
				<swiper-item class="navigation-swiper-item">
					<view class="swiper-item-top  " >
						<image src="../../static/navigation-icon/icon-car.png"></image>
						<text>断码清仓</text>
					</view>
					<view class="swiper-item-bottom  " >
						<image src="../../static/navigation-icon/icon-clock.png"></image>
						<text>限时秒杀</text>
					</view>
				</swiper-item>
				<swiper-item class="navigation-swiper-item">
					<view class="swiper-item-top  " >
						<image src="../../static/navigation-icon/icon-cloth.png"></image>
						<text>新衣馆</text>
					</view>
					<view class="swiper-item-bottom  ">
						<image src="../../static/navigation-icon/icon-medical.png"></image>
						<text>医药馆</text>
					</view>
				</swiper-item>
				<swiper-item class="navigation-swiper-item">
					<view class="swiper-item-top  " >
						<image src="../../static/navigation-icon/icon-vegetabke.png"></image>
						<text>免费水果</text>
					</view>
					<view class="swiper-item-bottom  " >
						<image src="../../static/navigation-icon/icon-cutdown.png"></image>
						<text>砍价</text>
					</view>
				</swiper-item>
				<swiper-item class="navigation-swiper-item">
					<view class="swiper-item-top  " >
						<image src="../../static/navigation-icon/icon-signin.png"></image>
						<text>现金签到</text>
					</view>
					<view class="swiper-item-bottom  " >
						<image src="../../static/navigation-icon/icon-cutdown.png"></image>
						<text>砍价</text>
					</view>
				</swiper-item>
				<swiper-item class="navigation-swiper-item">
					<view class="swiper-item-top  " >
						<image src="../../static/navigation-icon/icon-market.png"></image>
						<text>电器城</text>
					</view>
					<view class="swiper-item-bottom  " >
						<image src="../../static/navigation-icon/icon-red.png"></image>
						<text>天天领红包</text>
					</view>
				</swiper-item>
			</swiper>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			currentId: '' /* 控制被选中 */,
			currentIndex: '' /* 控制位置 */,
			title: 'Hello',
			brands: ['牛仔裤', '羽绒服', '皮鞋', '运动鞋', '跑步鞋', '篮球鞋', '围巾', '西装', '西裤']
		};
	},
	onLoad() {},
	methods: {
		handleScroll(index) {
			this.currentId = index;
			this.currentIndex = index;
			console.log(index);
		}
	}
};
</script>

<style lang="scss">
.right {
	width: 20upx;
	height: 20upx;
	border-top: 2upx solid #ababab;
	border-right: 2upx solid #ababab;
	transform: rotate(45deg);
}
.flex-row {
	display: flex;
	flex-direction: row;
	align-items: center;
}
.flex-coloum {
	display: flex;
	flex-direction: column;
	align-items: center;
}
.scroll-container {
	white-space: nowrap;
	height: 80upx;
	background: #fff;
	border-bottom: 1upx solid #ccc;
	.scroll-item {
		text-align: center;
		display: inline-block;
		margin: 0 30upx;
		line-height: 70upx;
		font-size: 36upx;
		font-weight: 400;
		color: #1e1e1e;

		&.active {
			color: #ff4f52;
			border-bottom: 10upx solid #ff4f52;
		}
	}
}

.invite {
	justify-content: space-between;
	padding: 10upx;
	margin: 0 20upx;
	width: calc(100% - 60upx);
	height: 50upx;
	border-bottom: 1upx solid #ccc;
	.invite-left {
		height: 100%;
		line-height: 50upx;
		image {
			margin-right: 6upx;
			width: 50upx;
			height: 50upx;
			vertical-align: middle;
		}
	}
	.invite-right {
		justify-content: space-between;
		color: #ababab;
		.invite-right-img {
			margin-right: 20upx;
			image {
				vertical-align: middle;
				width: 50upx;
				height: 50upx;
				border-radius: 50;
				background-color: white;
				border-radius: 50%;
				margin-right: -6upx;
			}
		}
		text {
			margin-right: 20upx;
		}
	}
}
.tab-navigation {
	background-color: red;
	padding: 20upx;
	width: calc(100% - 40upx);
	height: 350upx;
	.navigation-swiper {
		width: 100%;
		height: 100%;
		.navigation-swiper-item {
			width: 50upx;
			height: 100% !important;
			background-color: white;
			image {
				width: 100upx !important;
				height: 100upx !important;
			}
			text {
			}
			.swiper-item-top{
				display: flex;
				flex-direction: column;
				align-items: center;
				justify-content: space-between;
				height: 50%;
			}
			.swiper-item-bottom  {
				display: flex;
				flex-direction: column;
				align-items: center;
				justify-content: space-between;
				height: 50%;
			}
		}
	}
}
</style>
