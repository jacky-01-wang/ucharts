<template>
	<view class="" style="padding: 32rpx;">
		<wyb-table ref="table" first-line-fixed
		 :headers="headers" 
		 :contents="contents" 
		 @myEvent="getValue"
		 :height="auto" 
		 />
	</view>
	<!-- <view class="box">
		<view class="left">
			<block v-for="(item, index) in list" :key="index">
				<view class="Left_list">{{ item.name }}</view>
			</block>
		</view>
		<view class="table">
			<scroll-view scroll-x>
				<view class="header" v-for="(item, index) in listData" :key="index">
					<view class="table_one">{{ item.Name }}
					<text class="sanjiaoContainer" v-if="item.Name!==''"  @click="topSort">
						<text class="topSanjiao"  @click="topSort" data-type="top" :data-index="index">
							
						</text> 
						<text class="bottomSanjiao" @click="bottomSort" data-type="bottom" :data-index="index">
							
						</text>
					</text>
					</view>
					<view class="border">{{ item.NoNursing15 }}</view>
					<view class="border">{{ item.NoNursing30 }}</view>
					<view class="border">{{ item.advanceAchieve }}</view>
				</view>
			</scroll-view>
		</view>
	</view> -->
</template>
<script>
	import wybTable from '@/components/wyb-table/wyb-table.vue'
	export default {
	    components: {
	        wybTable
	    },
	    data() {
	        const theUrl = '/pages/demos/noticeBar-demo/more' // 本地的某个页面
	        const httpUrl = 'https://ext.dcloud.net.cn/plugin?id=2667' // 某个网址
	        return {
	            headers: [{
	                label: '学校名称',
	                key: 'name',
	            }, {
	                label: '在职教师',
	                key: 'age',
	            }, {
	                label: '付费学生',
	                key: 'moneyStudent',
	            }, {
	                label: '新增付费',
	                key: 'moneyAdd',
	            }],
	            contents: [{
	                name: '刘一',
	                age: '',
	                moneyStudent: '66',
	                moneyAdd: '99',
	                // url: ['查看更多', theUrl],
	            }, {
	                name: '陈二',
	                age: '18',
	                moneyStudent: '77',
	                moneyAdd: '98',
	                // url: ['我带参数', theUrl, {name: '陈二'}],
	            }, {
	                name: '张三',
	                age: '22',
	                moneyStudent: '55',
	                moneyAdd: '97',
	                // url: ['查看更多', theUrl],
	            }, {
	                name: '李四',
	                age: '19',
	                moneyStudent: '22',
	                moneyAdd: '96',
	                // url: '',
	            }, {
	                name: '王五',
	                age: '20',
	                moneyStudent: '10',
	                moneyAdd: '95',
	                // url: ['查看更多', theUrl],
	            }, {
	                name: '王六',
	                age: '20',
	                moneyStudent: '10',
	                moneyAdd: '95',
	                // url: ['查看更多', theUrl],
	            }, {
	                name: '王七',
	                age: '20',
	                moneyStudent: '10',
	                moneyAdd: '95',
	                // url: ['查看更多', theUrl],
	            }],
	            // urlCol: [{
	            //     type: 'route',
	            //     key: 'url'
	            // }, {
	            //     type: 'http',
	            //     key: 'link'
	            // }]
	        }
	    },
		methods:{
			sortByInt(array, key) {
			    array.sort(function (b, a) {
			        var x = a[key]
			        var y = b[key]
						return  x-y
			    })
				console.log(array)
			},
			sortByBottom(array, key){
				array.sort(function (b, a) {
				    var x = a[key]
				    var y = b[key]
						return  y-x
				})
			},
			getValue(value,type){
				
				if(value==1&&type=='top'){
					this.sortByInt(this.contents, "age")
					console.log("按age ( 数字 )排序：", )
				}
				if(value==2&&type=='top'){
					this.sortByInt(this.contents, "moneyStudent")
					console.log("按moneyStudent ( 数字 )排序：", )
				}
				if(value==3&&type=='top'){
					this.sortByInt(this.contents, "moneyAdd")
					console.log("按moneyAdd ( 数字 )排序：", )
				}
				if(value==1&&type=='bottom'){
					this.sortByBottom(this.contents, "age")
					console.log("按age ( 数字 )排序：", )
				}
				if(value==2&&type=='bottom'){
					this.sortByBottom(this.contents, "moneyStudent")
					console.log("按moneyStudent ( 数字 )排序：", )
				}
				if(value==3&&type=='bottom'){
					this.sortByBottom(this.contents, "moneyAdd")
					console.log("按moneyAdd ( 数字 )排序：", )
				}
				// console.log(value)
				// this.sortByInt(this.contents,'age' )
			}
		},
	// data() {
	// 	return {
	// 		list: [
	// 			{
	// 				name: ''
	// 			},
	// 			{
	// 				name: '金额'
	// 			},
	// 			{
	// 				name: '销量'
	// 			},
	// 			{
	// 				name: '金额占比'
	// 			}
	// 		],
	// 		listData: [
	// 			{ Name: '余淑金', NoNursing15: 123, NoNursing30: 0, advanceAchieve: 0 },
	// 			{ Name: '余淑金', NoNursing15: 456, NoNursing30: 456, advanceAchieve: 0 },
	// 			{ Name: '余淑金', NoNursing15: 12, NoNursing30: 0, advanceAchieve: 789 },
	// 			{ Name: '余淑金', NoNursing15: 50, NoNursing30: 0, advanceAchieve: 0 },
	// 			{ Name: '余淑金', NoNursing15: 0, NoNursing30: 0, advanceAchieve: 0 }
	// 		]
	// 	};
	// },
	// methods: {
	// 	sortByInt(array, key) {
	// 	    array.sort(function (b, a) {
	// 	        var x = a[key]
	// 	        var y = b[key]
	// 				return  x-y
	// 	    })
	// 		console.log(array)
	// 	},
	// 	topSort(e){
	// 		console.log(2548)
	// 		// this.currentIndex=e.currentTarget.dataset.index
	// 		// this.currentType=e.currentTarget.dataset.type
	// 		this.sortByInt(this.listData,'NoNursing15')
	// 		// this.$emit('myEvent',this.currentIndex,this.currentType)
	// 	},
	// 	// 点击
	// 	bottomSort(e){
	// 		console.log(e)
	// 		this.currentType=e.currentTarget.dataset.type
	// 		this.currentIndex=e.currentTarget.dataset.index
	// 		// this.$emit('myEvent',this.currentIndex,this.currentType)
	// 	},
	// }
};
</script>
<style lang="less" scoped>
	.sanjiaoContainer{
		display:inline-block;
		position:relative;
	}
	.topSanjiao{
		position:absolute;
		left:10upx;
		top:-25upx;
		display:inline-block;
		width: 0;
		height: 0;
		border-left: 10upx solid transparent;  /*左边框实现透明;10pupx是三角形左边框的宽度*/
		border-right: 10upx solid transparent;
		border-bottom: 15upx solid #000;
		
	}
	.bottomSanjiao {
		
		position:absolute;
		bottom:-10upx;
		left:10upx;
		display:inline-block;
		width: 0upx;                 /*  宽高设置为0，很重要，否则达不到效果 */
		height: 0upx;
		border-left: 10upx solid transparent;  /*左边框实现透明;10pupx是三角形左边框的宽度*/
		border-right: 10upx solid transparent;
		border-top: 15upx solid #000;
	}
page {
	font-size: 25upx;
	padding: 10upx;
}

.box {
	display: flex;
}

.left {
	width: 190upx;
	view:nth-last-of-type(1) {
		border-bottom: 1upx solid #c8c7cc;
	}
	.Left_list {
		height: 80upx;
		width: 180upx;
		text-align: center;
		line-height: 80upx;
		border: 1upx solid #c8c7cc;
		border-bottom: 0;
		border-right: 0;
	}
}

.table {
	white-space: nowrap;
	overflow: hidden;
	height: 100%;
	border: 1upx solid #c8c7cc;
	border-bottom: 0;
	.header {
		width: 190upx;
		text-align: center;
		display: inline-block;
		view {
			height: 80upx;
			border: 1upx solid #c8c7cc;
			border-top: 0;
			border-left: 0;
			line-height: 80upx;
		}
		.table_one {
			border-top: 0;
			border-left: 0;
			position: relative;
			.table_one_img {
				position: absolute;
				left: 0;
				top: 20upx;
				width: 5upx;
				height: 40upx;
				margin-right: 20upx;
			}
		}
	}
}

.border {
}
</style>

