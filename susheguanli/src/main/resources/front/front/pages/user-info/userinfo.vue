<template>
	<view class="content">
        <view class="box"
              :style='{"padding":"0","boxShadow":"0 0 0px rgba(0,0,0,0)","margin":"0","borderColor":"rgba(0,0,0,0)","backgroundColor":"#fff","borderRadius":"0","borderWidth":"0","width":"100%","borderStyle":"solid","height":"auto"}'>
		 <view v-if="tableName=='xuesheng'" class="cu-form-group">
			 <view class="title"
				   :style='{"width":"160rpx","fontSize":"28rpx","color":"var(--publicMainColor)","textAlign":"left"}'>账户
			 </view>
			 <input
					:style='{"padding":"0 30rpx","boxShadow":"0 0 0px rgba(0,0,0,.6) inset","margin":"0","borderColor":"var(--publicMainColor)","backgroundColor":"var(--publicSubColor)","color":"#fff","textAlign":"left","borderRadius":"20rpx 0","borderWidth":"0 10rpx","fontSize":"28rpx","borderStyle":"solid","height":"88rpx","marginTop":"7rpx"}'
					v-model="ruleForm.username" placeholder="账户"></input>
		 </view>
		 <view v-if="tableName=='xuesheng'" class="cu-form-group">
			 <view class="title"
				   :style='{"width":"160rpx","fontSize":"28rpx","color":"var(--publicMainColor)","textAlign":"left"}'>学生姓名
			 </view>
			 <input
					:style='{"padding":"0 30rpx","boxShadow":"0 0 0px rgba(0,0,0,.6) inset","margin":"0","borderColor":"var(--publicMainColor)","backgroundColor":"var(--publicSubColor)","color":"#fff","textAlign":"left","borderRadius":"20rpx 0","borderWidth":"0 10rpx","fontSize":"28rpx","borderStyle":"solid","height":"88rpx","marginTop":"7rpx"}'
					v-model="ruleForm.xueshengName" placeholder="学生姓名"></input>
		 </view>
		 <view v-if="tableName=='xuesheng'" class="cu-form-group">
			 <view class="title"
				   :style='{"width":"160rpx","fontSize":"28rpx","color":"var(--publicMainColor)","textAlign":"left"}'>学生手机号
			 </view>
			 <input
					:style='{"padding":"0 30rpx","boxShadow":"0 0 0px rgba(0,0,0,.6) inset","margin":"0","borderColor":"var(--publicMainColor)","backgroundColor":"var(--publicSubColor)","color":"#fff","textAlign":"left","borderRadius":"20rpx 0","borderWidth":"0 10rpx","fontSize":"28rpx","borderStyle":"solid","height":"88rpx","marginTop":"7rpx"}'
					v-model="ruleForm.xueshengPhone" placeholder="学生手机号"></input>
		 </view>
		 <view v-if="tableName=='xuesheng'" class="cu-form-group">
			 <view class="title"
				   :style='{"width":"160rpx","fontSize":"28rpx","color":"var(--publicMainColor)","textAlign":"left"}'>学生身份证号
			 </view>
			 <input
					:style='{"padding":"0 30rpx","boxShadow":"0 0 0px rgba(0,0,0,.6) inset","margin":"0","borderColor":"var(--publicMainColor)","backgroundColor":"var(--publicSubColor)","color":"#fff","textAlign":"left","borderRadius":"20rpx 0","borderWidth":"0 10rpx","fontSize":"28rpx","borderStyle":"solid","height":"88rpx","marginTop":"7rpx"}'
					v-model="ruleForm.xueshengIdNumber" placeholder="学生身份证号"></input>
		 </view>
			<view v-if="tableName=='xuesheng'" @tap="xueshengPhotoTap" class="cu-form-group">
				<view class="title"
					  :style='{"width":"160rpx","fontSize":"28rpx","color":"var(--publicMainColor)","textAlign":"left"}'>学生头像
				</view>
				<image
						:style='{"width":"76rpx","boxShadow":"0 0 0px rgba(0,0,0,.3)","borderRadius":"0","textAlign":"left","height":"76rpx"}'
						v-if="ruleForm.xueshengPhoto" class="avator" :src="baseUrl+ruleForm.xueshengPhoto" mode=""></image>
				<image
						:style='{"width":"76rpx","boxShadow":"0 0 0px rgba(0,0,0,.3)","borderRadius":"0","textAlign":"left","height":"76rpx"}'
						v-else class="avator" src="../../static/center/face.jpeg" mode=""></image>
			</view>
			<view v-if="tableName=='xuesheng'" class="cu-form-group select">
				<view :style='{"width":"160rpx","fontSize":"28rpx","color":"var(--publicMainColor)","textAlign":"left"}'
					  class="title">性别</view>
				<picker @change="xueshengsexTypesChange" :value="sexTypesIndex" :range="sexTypesOptions" range-key="indexName">
					<view :style='{"padding":"0 30rpx","boxShadow":"0 0 0px rgba(0,0,0,.6) inset","margin":"0","borderColor":"var(--publicMainColor)","backgroundColor":"var(--publicSubColor)","color":"#fff","textAlign":"left","borderRadius":"20rpx 0","borderWidth":"0 10rpx","fontSize":"28rpx","borderStyle":"solid","height":"88rpx","marginTop":"7rpx"}'
						  class="uni-input picker-select-input">{{ruleForm.sexValue?ruleForm.sexValue:"请选择性别"}}</view>
				</picker>
			</view>
		 <view v-if="tableName=='xuesheng'" class="cu-form-group">
			 <view class="title"
				   :style='{"width":"160rpx","fontSize":"28rpx","color":"var(--publicMainColor)","textAlign":"left"}'>学生邮箱
			 </view>
			 <input
					:style='{"padding":"0 30rpx","boxShadow":"0 0 0px rgba(0,0,0,.6) inset","margin":"0","borderColor":"var(--publicMainColor)","backgroundColor":"var(--publicSubColor)","color":"#fff","textAlign":"left","borderRadius":"20rpx 0","borderWidth":"0 10rpx","fontSize":"28rpx","borderStyle":"solid","height":"88rpx","marginTop":"7rpx"}'
					v-model="ruleForm.xueshengEmail" placeholder="学生邮箱"></input>
		 </view>

		<view class="btn" style="margin-top:40rpx">
			<view class="box" :style="{width: 'auto'}">
				<button @tap="update()" class="cu-btn lg"
					:style='{"margin":"0 30rpx 0 0","boxShadow":"0 0 16rpx rgba(0,0,0,0) inset","backgroundColor":"var(--publicMainColor)","borderColor":"var(--publicMainColor)","borderRadius":"8rpx","color":"#fff","borderWidth":"0","width":"auto","fontSize":"32rpx","borderStyle":"solid","height":"80rpx"}'>保存</button>
			</view>
		
			<view class="box" :style="{width: 'auto'}">
				<button @tap="logout()" class="cu-btn lg"
					:style='{"boxShadow":"0 0 16rpx rgba(0,0,0,0) inset","backgroundColor":"var(--publicMainColor)","borderColor":"#E6A23C","borderRadius":"8rpx","color":"#fff","borderWidth":"0px","width":"auto","fontSize":"28rpx","borderStyle":"solid","height":"80rpx"}'>退出登录</button>
			</view>
		</view>
	</view>
			<w-picker mode="dateTime" step="1" :current="false" :hasSecond="false" @confirm="createTimeConfirm"
					  ref="createTime" themeColor="#333333"></w-picker>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				ruleForm: {},
				tableName: "",
				sexTypesOptions: [],
				sexTypesIndex: 0,
				jinyongTypesOptions: [],
				jinyongTypesIndex: 0,
			}
		},
        computed: {
            baseUrl() {
                return this.$base.url;
            },
        },
		async onLoad() {
			let table = uni.getStorageSync("nowTable");
			let res = await this.$api.session(table);
			this.ruleForm = res.data;
			this.tableName = table;
			// 自定义下拉框值

			if (this.tableName == 'xuesheng') {
            let sex_typesParams = {
                page: 1,
                limit: 100,
                dicCode: 'sex_types',
            }
				let sex_typesRes = await this.$api.page(`dictionary`, sex_typesParams);

				this.sexTypesOptions = sex_typesRes.data.list
            let jinyong_typesParams = {
                page: 1,
                limit: 100,
                dicCode: 'jinyong_types',
            }
				let jinyong_typesRes = await this.$api.page(`dictionary`, jinyong_typesParams);

				this.jinyongTypesOptions = jinyong_typesRes.data.list
			}
			// this.styleChange()
		},
		methods: {
			// 下拉变化
			xueshengsexTypesChange(e) {
				this.sexTypesIndex = e.target.value
				this.ruleForm.sexValue = this.sexTypesOptions[this.sexTypesIndex].indexName
				this.ruleForm.sexTypes = this.sexTypesOptions[this.sexTypesIndex].codeIndex
			},
			// 下拉变化
			xueshengjinyongTypesChange(e) {
				this.jinyongTypesIndex = e.target.value
				this.ruleForm.jinyongValue = this.jinyongTypesOptions[this.jinyongTypesIndex].indexName
				this.ruleForm.jinyongTypes = this.jinyongTypesOptions[this.jinyongTypesIndex].codeIndex
			},
			// 日期控件
			createTimeConfirm(val) {
				this.ruleForm.createTime = val.result;
				this.$forceUpdate();
			},
			// 获取uuid
			getUUID() {
				return new Date().getTime();
			},
			logout() {
				uni.setStorageSync('token', '');
				this.$utils.jump('../login/login');
			},
			// 注册
			async update() {
					if ((!this.ruleForm.username) && `xuesheng` == this.tableName) {
						this.$utils.msg(`账户不能为空`);
						return
					}
					if ((!this.ruleForm.xueshengName) && `xuesheng` == this.tableName) {
						this.$utils.msg(`学生姓名不能为空`);
						return
					}
					if (`xuesheng` == this.tableName && this.ruleForm.xuesheng && (!this.$validate.isMobile(this
									.ruleForm.xueshengPhone))) {
						this.$utils.msg(`学生手机号应输入正确格式`);
						return
					}
					if (`xuesheng` == this.tableName && this.ruleForm.xuesheng && (!this.$validate.checkIdCard(this
									.ruleForm.xueshengIdNumber))) {
						this.$utils.msg(`学生身份证号应输入正确格式`);
						return
					}
					if ((!this.ruleForm.xueshengPhoto) && `xuesheng` == this.tableName) {
						this.$utils.msg(`学生头像不能为空`);
						return
					}
					if (`xuesheng` == this.tableName && this.ruleForm.xuesheng && (!this.$validate.isEmail(this
                                    .ruleForm.xueshengEmail))) {
                        this.$utils.msg(`学生邮箱应输入正确格式`);
                        return
                    }

					let table = uni.getStorageSync("nowTable");
					await this.$api.update(table, this.ruleForm);
					this.$utils.msgBack('修改成功');
			},
			xueshengPhotoTap() {
				let _this = this;
				this.$api.upload(function(res) {
					_this.ruleForm.xueshengPhoto = 'upload/' + res.file;
					_this.$forceUpdate();
				});
			},
            toggleTab(str) {
                this.$refs[str].show();
            }

		}
	}
</script>
<style lang="scss" scoped>
    .content:after {
        position: fixed;
        top: 0;
        right: 0;
        left: 0;
        bottom: 0;
        content: '';
        background-attachment: fixed;
        background-size: cover;
        background-position: center;
    }

    .avator {
        width: 110 upx;
        height: 110 upx;
        border-radius: 50%;
        margin-left: 30 upx;
    }

    .cu-form-group.active {
        justify-content: space-between;
    }

    .cu-btn {
        width: 100%;
    }

    .cu-form-group .title {
        height: auto;
        line-height:30rpx
    }

    .right-input {
        flex: 1;
        text-align: left;
        line-height: 52 rpx;
    }

    .btn {
        display: flex;
        align-items: center;
        justify-content: center;
        flex-wrap: wrap;
    }

    .box {
        width: auto;
        padding: 0 10 upx;
        box-sizing: border-box;
        margin-bottom: 20 upx;
    }

    .picker-select-input {
        line-height: 52 rpx;
    }
</style>
