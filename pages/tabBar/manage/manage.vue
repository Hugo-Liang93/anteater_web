<template>
	<view>
		<template v-for="fun in functionList">
			<uni-section :title="fun.functionName" type="line"></uni-section>
			<view class="example-body">
				<uni-grid :column="3" :highlight="true" @change="change">
					<uni-grid-item v-for="(item, index) in fun.subFunction" :index="index" :key="index">
						<view class="grid-item-box">
							<!-- <image :src="" class="image" mode="aspectFill" /> -->
							<text class="text">{{ item.text }}</text>
						</view>
					</uni-grid-item>
				</uni-grid>
			</view>
		</template>
	</view>
</template>

<script>
	import uniSection from '@/components/uni-section/uni-section.vue'
	import uniGrid from "@/components/uni-grid/uni-grid.vue"
	import uniGridItem from "@/components/uni-grid-item/uni-grid-item.vue"
	export default {
		components: {
			uniGrid,
			uniGridItem,
			uniSection
		},
		data() {
			return {
				functionList: {
					baseInfo: {
						functionName: '基础信息录入',
						subFunction: [{
								text: '房东信息登记',
								functionId: 1,
							},
							{
								text: '房屋信息登记',
								functionId: 2

							},
							{
								text: '租客信息登记',
								functionId: 3
							},
							{
								text: "客房信息登记",
								functionId: 4
							},
							{
								text: "杂项单价登记",
								functionId: 5
							}
						]
					},
					roomInfo: {
						functionName: '房屋出租信息登记' ,
						subFunction:[{
							text: "客房出租信息登记",
							functionId: 6
						}]
					},
					dailyInfo: {
						functionName: '日常信息录入',
						subFunction:[{
							text: "账单信息录入",
							functionId: 7
						}]
					},
					storage:{
						functionName: '物资情况',
						subFunction:[]
					}
				}
			}

		},
		methods: {
			change(e) {
				let {
					index
				} = e.detail

				uni.showToast({
					title: `点击第${index+1}个宫格`,
					icon: 'none'
				})
			}
		}
	}
</script>

<style>
	.example-body {
		flex-direction: column;
		padding: 15px;
		background-color: #ffffff;
	}

	.grid-item-box {
		/* 属性是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto */
		/* 如果所有项目的flex-grow属性都为1，
		则它们将等分剩余空间（如果有的话）。如果一个项目的flex-grow属性为2，
		其他项目都为1，则前者占据的剩余空间将比其他项多一倍。 */
		flex: 1;
		/* position: relative;*/
		/* #ifndef APP-NVUE */
		display: flex;
		/* #endif */
		/* 水平方向 从左往右排列  */
		flex-direction: column;
		align-items: center;
		justify-content: center;
		padding: 15px 0;
	}
</style>
