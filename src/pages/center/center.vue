<template>
<div class="center-preview" :style='{"width":"80%","margin":"10px auto","position":"relative","background":"none"}'>
	<div class="title" :style='{"border":"2px solid #57A7A5","margin":"0","color":"#57A7A5","textAlign":"center","background":"#fff","fontSize":"20px","lineHeight":"44px"}'>{{ title }}</div>
	
	<div class="info" :style='{"padding":"50px 50px 50px 280px","boxShadow":"none","margin":"0 auto 20px","borderRadius":"0","flexWrap":"wrap","background":"#ffffff","display":"flex","width":"100%","position":"relative","height":"260px"}'>
		<div :style='{"borderColor":"#efefef","color":"#333","borderWidth":"0 0 1px 0","display":"none","width":"100%","lineHeight":"44px","fontSize":"15px","borderStyle":"solid","height":"44px"}'>个人信息</div>
		<div :style='{"borderColor":"#efefef","top":"45px","left":"100px","borderWidth":"0","width":"150px","fontSize":"0","position":"absolute","borderStyle":"solid","height":"150px"}' v-if="userTableName=='yonghu'">
			<el-image :style='{"margin":"10px auto","borderColor":"#efefef","objectFit":"cover","borderRadius":"10px","borderWidth":"0 0 1px 0","display":"block","width":"100%","borderStyle":"solid","height":"100%"}' :src="sessionForm.touxiang?baseUrl + sessionForm.touxiang:require('@/assets/avator.png')" fit="cover"></el-image>
		</div>
		<div :style='{"borderColor":"#efefef","top":"45px","left":"100px","borderWidth":"0","width":"150px","fontSize":"0","position":"absolute","borderStyle":"solid","height":"150px"}' v-if="userTableName=='fangchanjingli'">
			<el-image :style='{"margin":"10px auto","borderColor":"#efefef","objectFit":"cover","borderRadius":"10px","borderWidth":"0 0 1px 0","display":"block","width":"100%","borderStyle":"solid","height":"100%"}' :src="sessionForm.touxiang?baseUrl + sessionForm.touxiang:require('@/assets/avator.png')" fit="cover"></el-image>
		</div>
		<div :style='{"padding":"0 0","borderColor":"#efefef","flexWrap":"wrap","borderWidth":"0","flexDirection":"column","display":"flex","width":"calc(100% / 3)","lineHeight":"40px","borderStyle":"solid","height":"50%"}' v-if="userTableName=='yonghu'">
			<span class="icon iconfont icon-shouye-zhihui" :style='{"padding":"0 5px","color":"#fff","borderRadius":"50%","textAlign":"center","background":"#57A7A5","display":"none","width":"55px","fontSize":"24px","lineHeight":"55px","height":"55px"}'></span>
			<div :style='{"color":"#333","fontSize":"14px","display":"none"}'>用户账号</div>
			<div :style='{"fontSize":"24px","color":"#000","textAlign":"left","flex":1}'>{{sessionForm.yonghuzhanghao}}</div>
		</div>
		<div :style='{"padding":"0 0","borderColor":"#efefef","flexWrap":"wrap","borderWidth":"0","flexDirection":"column","display":"flex","width":"calc(100% / 3)","lineHeight":"40px","borderStyle":"solid","height":"50%"}' v-if="userTableName=='yonghu'">
			<span class="icon iconfont icon-qita1" :style='{"padding":"0 0","margin":"10px","color":"#fff","borderRadius":"50%","textAlign":"center","background":"#57A7A5","width":"55px","fontSize":"24px","lineHeight":"55px","height":"55px"}'></span>
			<div :style='{"width":"calc(100% - 75px)","fontSize":"16px","color":"#000","height":"50%"}'>用户姓名</div>
			<div :style='{"width":"calc(100% - 75px)","fontSize":"15px","color":"#333","textAlign":"left","flex":1,"height":"50%"}'>{{sessionForm.yonghuxingming}}</div>
		</div>
		<div :style='{"padding":"0 0","borderColor":"#efefef","flexWrap":"wrap","borderWidth":"0","flexDirection":"column","display":"flex","width":"calc(100% / 3)","lineHeight":"40px","borderStyle":"solid","height":"50%"}' v-if="userTableName=='yonghu'">
			<span class="icon iconfont icon-baohuhaoma" :style='{"padding":"0 0","margin":"10px","color":"#fff","borderRadius":"50%","textAlign":"center","background":"#57A7A5","width":"55px","fontSize":"24px","lineHeight":"55px","height":"55px"}'></span>
			<div :style='{"width":"calc(100% - 75px)","fontSize":"16px","color":"#000","height":"50%"}'>性别</div>
			<div :style='{"width":"calc(100% - 75px)","fontSize":"15px","color":"#333","textAlign":"left","flex":1,"height":"50%"}'>{{sessionForm.xingbie}}</div>
		</div>
		<div :style='{"padding":"0 0","borderColor":"#efefef","borderWidth":"0","display":"flex","width":"calc(100% / 3)","lineHeight":"40px","borderStyle":"solid","height":"75px"}' v-if="userTableName=='yonghu'">
			<span class="icon iconfont icon-shouye-zhihui" :style='{"padding":"0 5px","fontSize":"14px","color":"#333","display":"none"}'></span>
			<div :style='{"color":"#333","fontSize":"14px","display":"none"}'>电话号码</div>
			<div :style='{"fontSize":"16px","color":"#000","textAlign":"left","flex":1}'>{{sessionForm.dianhuahaoma}}</div>
		</div>
		<div :style='{"padding":"0 0","borderColor":"#efefef","flexWrap":"wrap","borderWidth":"0","flexDirection":"column","display":"flex","width":"calc(100% / 3)","lineHeight":"40px","borderStyle":"solid","height":"50%"}' v-if="userTableName=='yonghu'">
			<span class="icon iconfont icon-kuaijiezhifu" :style='{"padding":"0 0","margin":"10px","color":"#fff","borderRadius":"50%","textAlign":"center","background":"#57A7A5","width":"55px","fontSize":"24px","lineHeight":"55px","height":"55px"}'></span>
			<div :style='{"width":"calc(100% - 75px)","fontSize":"16px","color":"#000","height":"50%"}'>身份证</div>
			<div :style='{"width":"calc(100% - 75px)","fontSize":"14px","color":"#333","textAlign":"left","height":"50%"}'>{{sessionForm.shenfenzheng}}</div>
		</div>
		<div :style='{"padding":"0 0","borderColor":"#efefef","flexWrap":"wrap","borderWidth":"0","flexDirection":"column","display":"flex","width":"calc(100% / 3)","lineHeight":"40px","borderStyle":"solid","height":"50%"}' v-if="userTableName=='fangchanjingli'">
			<span class="icon iconfont icon-shouye-zhihui" :style='{"padding":"0 5px","color":"#fff","borderRadius":"50%","textAlign":"center","background":"#57A7A5","display":"none","width":"55px","fontSize":"24px","lineHeight":"55px","height":"55px"}'></span>
			<div :style='{"color":"#333","fontSize":"14px","display":"none"}'>经理账号</div>
			<div :style='{"fontSize":"24px","color":"#000","textAlign":"left","flex":1}'>{{sessionForm.jinglizhanghao}}</div>
		</div>
		<div :style='{"padding":"0 0","borderColor":"#efefef","flexWrap":"wrap","borderWidth":"0","flexDirection":"column","display":"flex","width":"calc(100% / 3)","lineHeight":"40px","borderStyle":"solid","height":"50%"}' v-if="userTableName=='fangchanjingli'">
			<span class="icon iconfont icon-qita1" :style='{"padding":"0 0","margin":"10px","color":"#fff","borderRadius":"50%","textAlign":"center","background":"#57A7A5","width":"55px","fontSize":"24px","lineHeight":"55px","height":"55px"}'></span>
			<div :style='{"width":"calc(100% - 75px)","fontSize":"16px","color":"#000","height":"50%"}'>经理姓名</div>
			<div :style='{"width":"calc(100% - 75px)","fontSize":"15px","color":"#333","textAlign":"left","flex":1,"height":"50%"}'>{{sessionForm.jinglixingming}}</div>
		</div>
		<div :style='{"padding":"0 0","borderColor":"#efefef","flexWrap":"wrap","borderWidth":"0","flexDirection":"column","display":"flex","width":"calc(100% / 3)","lineHeight":"40px","borderStyle":"solid","height":"50%"}' v-if="userTableName=='fangchanjingli'">
			<span class="icon iconfont icon-baohuhaoma" :style='{"padding":"0 0","margin":"10px","color":"#fff","borderRadius":"50%","textAlign":"center","background":"#57A7A5","width":"55px","fontSize":"24px","lineHeight":"55px","height":"55px"}'></span>
			<div :style='{"width":"calc(100% - 75px)","fontSize":"16px","color":"#000","height":"50%"}'>性别</div>
			<div :style='{"width":"calc(100% - 75px)","fontSize":"15px","color":"#333","textAlign":"left","flex":1,"height":"50%"}'>{{sessionForm.xingbie}}</div>
		</div>
		<div :style='{"padding":"0 0","borderColor":"#efefef","borderWidth":"0","display":"flex","width":"calc(100% / 3)","lineHeight":"40px","borderStyle":"solid","height":"75px"}' v-if="userTableName=='fangchanjingli'">
			<span class="icon iconfont icon-shouye-zhihui" :style='{"padding":"0 5px","fontSize":"14px","color":"#333","display":"none"}'></span>
			<div :style='{"color":"#333","fontSize":"14px","display":"none"}'>年龄</div>
			<div :style='{"fontSize":"16px","color":"#000","textAlign":"left","flex":1}'>{{sessionForm.nianling}}</div>
		</div>
		<div :style='{"padding":"0 0","borderColor":"#efefef","flexWrap":"wrap","borderWidth":"0","flexDirection":"column","display":"flex","width":"calc(100% / 3)","lineHeight":"40px","borderStyle":"solid","height":"50%"}' v-if="userTableName=='fangchanjingli'">
			<span class="icon iconfont icon-kuaijiezhifu" :style='{"padding":"0 0","margin":"10px","color":"#fff","borderRadius":"50%","textAlign":"center","background":"#57A7A5","width":"55px","fontSize":"24px","lineHeight":"55px","height":"55px"}'></span>
			<div :style='{"width":"calc(100% - 75px)","fontSize":"16px","color":"#000","height":"50%"}'>电话号码</div>
			<div :style='{"width":"calc(100% - 75px)","fontSize":"14px","color":"#333","textAlign":"left","height":"50%"}'>{{sessionForm.dianhuahaoma}}</div>
		</div>
		<div :style='{"padding":"0 0","borderColor":"#efefef","flexWrap":"wrap","borderWidth":"0","flexDirection":"column","display":"flex","width":"calc(100% / 3)","lineHeight":"40px","borderStyle":"solid","height":"50%"}' v-if="userTableName=='fangchanjingli'">
			<span class="icon iconfont icon-tongji2" :style='{"padding":"0 5px","margin":"10px","color":"#fff","borderRadius":"50%","textAlign":"center","background":"#57A7A5","width":"55px","fontSize":"24px","lineHeight":"55px","height":"55px"}'></span>
			<div :style='{"width":"calc(100% - 75px)","fontSize":"16px","color":"#000","height":"50%"}'>专业资质</div>
			<div :style='{"width":"calc(100% - 75px)","fontSize":"15px","color":"#333","textAlign":"left","flex":1,"height":"50%"}'>{{sessionForm.zhuanyezizhi}}</div>
		</div>
		
	</div>
	
    <el-tabs tab-position="left" :style='{"width":"100%","flexWrap":"wrap","background":"#fff","justifyContent":"center","display":"flex"}' @tab-click="handleClick">
      <el-tab-pane label="个人中心">
        <el-form class="center-preview-pv" ref="sessionForm" :model="sessionForm" :rules="rules" label-width="200px">
          <el-form-item :style='{"padding":"10px","margin":"0 0 10px","background":"none"}' v-if="userTableName=='yonghu'" label="用户账号" prop="yonghuzhanghao">
            <el-input v-model="sessionForm.yonghuzhanghao" placeholder="用户账号" readonly></el-input>
          </el-form-item>
          <el-form-item :style='{"padding":"10px","margin":"0 0 10px","background":"none"}' v-if="userTableName=='yonghu'" label="用户姓名" prop="yonghuxingming">
            <el-input v-model="sessionForm.yonghuxingming" placeholder="用户姓名" ></el-input>
          </el-form-item>
          <el-form-item :style='{"padding":"10px","margin":"0 0 10px","background":"none"}' v-if="userTableName=='yonghu'" label="性别">
            <el-select v-model="sessionForm.xingbie" placeholder="请选择性别" >
              <el-option v-for="(item, index) in dynamicProp.xingbie" :key="index" :label="item" :value="item"></el-option>
            </el-select>
          </el-form-item>
          <el-form-item :style='{"padding":"10px","margin":"0 0 10px","background":"none"}' v-if="userTableName=='yonghu'" label="头像">
			<file-upload
			tip="点击上传头像"
			action="file/upload"
			:limit="1"
			:multiple="true"
			:fileUrls="sessionForm.touxiang?sessionForm.touxiang:''"
			@change="yonghutouxiangHandleAvatarSuccess"
			></file-upload>
          </el-form-item>
          <el-form-item :style='{"padding":"10px","margin":"0 0 10px","background":"none"}' v-if="userTableName=='yonghu'" label="电话号码" prop="dianhuahaoma">
            <el-input v-model="sessionForm.dianhuahaoma" placeholder="电话号码" ></el-input>
          </el-form-item>
          <el-form-item :style='{"padding":"10px","margin":"0 0 10px","background":"none"}' v-if="userTableName=='yonghu'" label="身份证" prop="shenfenzheng">
            <el-input v-model="sessionForm.shenfenzheng" placeholder="身份证" ></el-input>
          </el-form-item>
          <el-form-item :style='{"padding":"10px","margin":"0 0 10px","background":"none"}' v-if="userTableName=='fangchanjingli'" label="经理账号" prop="jinglizhanghao">
            <el-input v-model="sessionForm.jinglizhanghao" placeholder="经理账号" readonly></el-input>
          </el-form-item>
          <el-form-item :style='{"padding":"10px","margin":"0 0 10px","background":"none"}' v-if="userTableName=='fangchanjingli'" label="经理姓名" prop="jinglixingming">
            <el-input v-model="sessionForm.jinglixingming" placeholder="经理姓名" ></el-input>
          </el-form-item>
          <el-form-item :style='{"padding":"10px","margin":"0 0 10px","background":"none"}' v-if="userTableName=='fangchanjingli'" label="性别">
            <el-select v-model="sessionForm.xingbie" placeholder="请选择性别" >
              <el-option v-for="(item, index) in dynamicProp.xingbie" :key="index" :label="item" :value="item"></el-option>
            </el-select>
          </el-form-item>
          <el-form-item :style='{"padding":"10px","margin":"0 0 10px","background":"none"}' v-if="userTableName=='fangchanjingli'" label="头像">
			<file-upload
			tip="点击上传头像"
			action="file/upload"
			:limit="1"
			:multiple="true"
			:fileUrls="sessionForm.touxiang?sessionForm.touxiang:''"
			@change="fangchanjinglitouxiangHandleAvatarSuccess"
			></file-upload>
          </el-form-item>
          <el-form-item :style='{"padding":"10px","margin":"0 0 10px","background":"none"}' v-if="userTableName=='fangchanjingli'" label="年龄" prop="nianling">
            <el-input v-model="sessionForm.nianling" placeholder="年龄" ></el-input>
          </el-form-item>
          <el-form-item :style='{"padding":"10px","margin":"0 0 10px","background":"none"}' v-if="userTableName=='fangchanjingli'" label="电话号码" prop="dianhuahaoma">
            <el-input v-model="sessionForm.dianhuahaoma" placeholder="电话号码" ></el-input>
          </el-form-item>
          <el-form-item :style='{"padding":"10px","margin":"0 0 10px","background":"none"}' v-if="userTableName=='fangchanjingli'" label="专业资质" prop="zhuanyezizhi">
            <el-input v-model="sessionForm.zhuanyezizhi" placeholder="专业资质" ></el-input>
          </el-form-item>
          <el-form-item :style='{"padding":"0","margin":"0"}'>
            <el-button :style='{"border":"0","cursor":"pointer","padding":"0","margin":"0 20px 0 0","outline":"none","color":"rgba(255, 255, 255, 1)","borderRadius":"0","background":"#57A7A5","width":"128px","lineHeight":"40px","fontSize":"14px","height":"40px"}' type="primary" @click="onSubmit('sessionForm')">更新信息</el-button>
            <el-button :style='{"border":"none","cursor":"pointer","padding":"0","margin":"0","outline":"none","color":"#fff","borderRadius":"0","background":"#9E9E9E","width":"128px","lineHeight":"40px","fontSize":"14px","height":"40px"}' type="danger" @click="logout">退出登录</el-button>
          </el-form-item>
        </el-form>
      </el-tab-pane>
	  <el-tab-pane label="修改密码">
		<el-form class="center-preview-pv" ref="passwordForm" :model="passwordForm" :rules="passwordRules" label-width="200px">
			<el-form-item :style='{"padding":"10px","margin":"0 0 10px","background":"none"}' label="原密码" prop="password">
			  <el-input type="password" v-model="passwordForm.password" placeholder="原密码"></el-input>
			</el-form-item>
			<el-form-item :style='{"padding":"10px","margin":"0 0 10px","background":"none"}' label="新密码" prop="newpassword">
			  <el-input type="password" v-model="passwordForm.newpassword" placeholder="新密码"></el-input>
			</el-form-item>
			<el-form-item :style='{"padding":"10px","margin":"0 0 10px","background":"none"}' label="确认密码" prop="repassword">
			  <el-input type="password" v-model="passwordForm.repassword" placeholder="确认密码"></el-input>
			</el-form-item>
			<el-form-item :style='{"padding":"0","margin":"0"}'>
			  <el-button :style='{"border":"0","cursor":"pointer","padding":"0","margin":"0 20px 0 0","outline":"none","color":"rgba(255, 255, 255, 1)","borderRadius":"0","background":"#57A7A5","width":"128px","lineHeight":"40px","fontSize":"14px","height":"40px"}' type="primary" @click="updatePassword">修改密码</el-button>
			</el-form-item>
		</el-form>
	  </el-tab-pane>
		<el-tab-pane v-for="(item,index) in menuList" :key="index" v-if="hasBack(item.menu)" :label="item.child[0].menu" :name="item.child[0].tableName"></el-tab-pane>
      <el-tab-pane label="我的收藏"></el-tab-pane>
    </el-tabs>

</div>
</template>

<script>
  import config from '@/config/config'
  import menu from '@/config/menu'
  import Vue from 'vue'
  export default {
    //数据集合
    data() {
      return {
        title: '个人中心',
        baseUrl: config.baseUrl,
        sessionForm: {},
		passwordForm: {},
		passwordRules: {
			password: [
				{
					required: true,
					message: "密码不能为空",
					trigger: "blur"
				}
			],
			newpassword: [
				{
					required: true,
					message: "新密码不能为空",
					trigger: "blur"
				}
			],
			repassword: [
				{
					required: true,
					message: "确认密码不能为空",
					trigger: "blur"
				}
			]
		},
        rules: {},
		menuList: [],
        disabled: false,
        uploadUrl: config.baseUrl + 'file/upload',
        imageUrl: '',
        headers: {Token: localStorage.getItem('frontToken')},
        userTableName: localStorage.getItem('UserTableName'),
        dynamicProp: {},
      }
    },
    created() {
		let menus = menu.list()
		for(let x in menus){
			if(menus[x].tableName == this.userTableName){
				this.menuList = menus[x].backMenu
			}
		}
		if ('yonghu' == this.userTableName) {
			this.$set(this.sessionForm, 'yonghuzhanghao', null);
		}
		if ('yonghu' == this.userTableName) {
			this.$set(this.sessionForm, 'yonghuxingming', null);
		}
		if ('yonghu' == this.userTableName) {
			this.$set(this.sessionForm, 'mima', null);
		}
		if ('yonghu' == this.userTableName) {
			this.$set(this.sessionForm, 'xingbie', null);
		}
		if ('yonghu' == this.userTableName) {
			this.$set(this.sessionForm, 'touxiang', null);
		}
		if ('yonghu' == this.userTableName) {
			this.$set(this.sessionForm, 'dianhuahaoma', null);
		}
		if ('yonghu' == this.userTableName) {
			this.$set(this.sessionForm, 'shenfenzheng', null);
		}
		if ('fangchanjingli' == this.userTableName) {
			this.$set(this.sessionForm, 'jinglizhanghao', null);
		}
		if ('fangchanjingli' == this.userTableName) {
			this.$set(this.sessionForm, 'jinglixingming', null);
		}
		if ('fangchanjingli' == this.userTableName) {
			this.$set(this.sessionForm, 'mima', null);
		}
		if ('fangchanjingli' == this.userTableName) {
			this.$set(this.sessionForm, 'xingbie', null);
		}
		if ('fangchanjingli' == this.userTableName) {
			this.$set(this.sessionForm, 'touxiang', null);
		}
		if ('fangchanjingli' == this.userTableName) {
			this.$set(this.sessionForm, 'nianling', null);
		}
		if ('fangchanjingli' == this.userTableName) {
			this.$set(this.sessionForm, 'dianhuahaoma', null);
		}
		if ('fangchanjingli' == this.userTableName) {
			this.$set(this.sessionForm, 'zhuanyezizhi', null);
		}

      if ('yonghu' == this.userTableName) {
        this.$set(this.rules, 'yonghuzhanghao', [{ required: true, message: '请输入用户账号', trigger: 'blur' }]);
      }
      if ('yonghu' == this.userTableName) {
        this.$set(this.rules, 'yonghuxingming', [{ required: true, message: '请输入用户姓名', trigger: 'blur' }]);
      }
      if ('yonghu' == this.userTableName) {
        this.$set(this.rules, 'mima', [{ required: true, message: '请输入密码', trigger: 'blur' }]);
      }
			if ('yonghu' == this.userTableName) {
        this.$set(this.rules, 'dianhuahaoma', [{ required: false, validator: this.$validate.isMobile, trigger: 'blur' }]);
      }
      if ('fangchanjingli' == this.userTableName) {
        this.$set(this.rules, 'jinglizhanghao', [{ required: true, message: '请输入经理账号', trigger: 'blur' }]);
      }
      if ('fangchanjingli' == this.userTableName) {
        this.$set(this.rules, 'jinglixingming', [{ required: true, message: '请输入经理姓名', trigger: 'blur' }]);
      }
      if ('fangchanjingli' == this.userTableName) {
        this.$set(this.rules, 'mima', [{ required: true, message: '请输入密码', trigger: 'blur' }]);
      }
			if ('fangchanjingli' == this.userTableName) {
        this.$set(this.rules, 'nianling', [{ required: false, validator: this.$validate.isIntNumer, trigger: 'blur' }]);
      }
			if ('fangchanjingli' == this.userTableName) {
        this.$set(this.rules, 'dianhuahaoma', [{ required: false, validator: this.$validate.isMobile, trigger: 'blur' }]);
      }

      this.init();
      this.sessionForm = JSON.parse(localStorage.getItem('sessionForm'))
    },
    //方法集合
    methods: {
      init() {
        if ('yonghu' == this.userTableName) {
          this.dynamicProp.xingbie = '男,女'.split(',');
        }
        if ('fangchanjingli' == this.userTableName) {
          this.dynamicProp.xingbie = '男,女'.split(',');
        }
      },
	  setSession(){
		  localStorage.setItem('sessionForm',JSON.stringify(this.sessionForm))
	  },
      onSubmit(formName) {
		if(`yonghu` == this.userTableName && this.sessionForm.touxiang!=null){
			this.sessionForm.touxiang = this.sessionForm.touxiang.replace(new RegExp(this.$config.baseUrl,"g"),"");
		}
		if(`fangchanjingli` == this.userTableName && this.sessionForm.touxiang!=null){
			this.sessionForm.touxiang = this.sessionForm.touxiang.replace(new RegExp(this.$config.baseUrl,"g"),"");
		}
        this.$refs[formName].validate((valid) => {
			if (valid) {
				this.$http.post(this.userTableName + '/update', this.sessionForm).then(res => {
					if (res.data.code == 0) {
						this.setSession()
						this.$message({
							message: '更新成功',
							type: 'success',
							duration: 1500
						});
					}
				});
			} else {
				return false;
			}
        });
      },
      yonghutouxiangHandleAvatarSuccess(fileUrls) {
        this.sessionForm.touxiang = fileUrls;
      },
      fangchanjinglitouxiangHandleAvatarSuccess(fileUrls) {
        this.sessionForm.touxiang = fileUrls;
      },
      handleClick(tab, event) {
        switch(event.target.outerText) {
          case '个人中心':
            tab.$router.push('/index/center');
            break;
          case '修改密码':
            this.passwordForm = {
				password: '',
				newpassword: '',
				repassword: '',
			}
			this.$forceUpdate()
            break;
          case '我的收藏':
            localStorage.setItem('storeupType', 1);
            tab.$router.push('/index/storeup');
            break;
		  default:
		  	tab.$router.push(`/index/${tab.name}?centerType=1`);
        }

        this.title = event.target.outerText;
      },
	  async updatePassword(){
			this.$refs["passwordForm"].validate(async valid => {
				if (valid) {
					var password = "";
					if (this.sessionForm.mima) {
						password = this.sessionForm.mima;
					} else if (this.sessionForm.password) {
						password = this.sessionForm.password;
					}
					if (this.passwordForm.password != password) {
						this.$message.error("原密码错误");
						return;
					}
					if (this.passwordForm.newpassword != this.passwordForm.repassword) {
						this.$message.error("两次密码输入不一致");
						return;
					}
					if (this.userTableName == 'yonghu') {
					}
					this.sessionForm.password = this.passwordForm.newpassword;
					this.sessionForm.mima = this.passwordForm.newpassword;
					this.$http.post(`${this.userTableName}/update`,this.sessionForm).then(({data})=>{
						if (data && data.code === 0) {
							this.$message({
								message: "修改密码成功,下次登录系统生效",
								type: "success",
								duration: 1500,
								onClose: () => {
								}
							});
							this.setSession()
						} else {
							this.$message.error(data.msg);
						}
					});
				}
			})
	  },
      logout() {
        localStorage.clear();
        Vue.http.headers.common['Token'] = "";
        this.$router.push('/index/home');
        this.activeIndex = '0'
        localStorage.setItem('keyPath', this.activeIndex)
        this.$forceUpdate()
        this.$message({
            message: '登出成功',
            type: 'success',
            duration: 1500,
        });
      },
	  hasBack(name){
		  switch(name){
			case '我的收藏管理':
				return false
				break;
			default:
				return true
		  }
	  }
    }
  }
</script>

<style rel="stylesheet/scss" lang="scss" scoped>
  .center-preview {
  
    .el-tabs {
      & /deep/ .el-tabs__header {
		.el-tabs__nav{
			overflow: auto;
		}
		::-webkit-scrollbar {
		  -webkit-appearance: none;
		  width: 6px;
		  height: 6px;
		}
		::-webkit-scrollbar-track {
		  background: rgba(0, 0, 0, 0.1);
		  border-radius: 0;
		}
		::-webkit-scrollbar-thumb {
		  cursor: pointer;
		  border-radius: 5px;
		  background: rgba(0, 0, 0, 0.15);
		  transition: color 0.2s ease;
		}
		::-webkit-scrollbar-thumb:hover {
		  background: rgba(0, 0, 0, 0.3);
		}
        .el-tabs__nav-wrap {
          margin: 0;
  
          &::after {
            content: none;
          }
        }
  
        .el-tabs__active-bar {
          display: none !important;
        }
      }
  
      .center-preview-pv {
        .el-date-editor.el-input {
          width: auto;
        }
  
        .balance {
          .el-input {
            width: auto;
          }
        }
      }
    }
  }
  
  .center-preview .el-tabs /deep/ .el-tabs__header {
	padding: 0;
	margin: 0 auto;
	background: #57A7A5;
	width: 100%;
	border-color: #eee;
	border-width: 0;
	position: relative;
	float: left;
	border-style: solid;
  }
  
  .center-preview .el-tabs /deep/ .el-tabs__header .el-tabs__item {
  	padding: 0 30px;
  	color: #000;
  	background: #57A7A5;
  	font-weight: 500;
  	display: inline-block;
  	font-size: 14px;
  	line-height: 60px;
  	position: relative;
  	text-align: center;
  	height: 60px;
  }
  
  .center-preview .el-tabs /deep/ .el-tabs__header .el-tabs__item:hover {
  	padding: 0 30px;
  	color: #fff;
  	background: #57A7A5;
  	font-weight: 500;
  	display: inline-block;
  	font-size: 14px;
  	line-height: 60px;
  	position: relative;
  	text-align: center;
  	height: 60px;
  }
  
  .center-preview .el-tabs /deep/ .el-tabs__header .el-tabs__item.is-active {
  	padding: 0 30px;
  	color: #fff;
  	background: #57A7A5;
  	font-weight: 500;
  	display: inline-block;
  	font-size: 14px;
  	line-height: 60px;
  	position: relative;
  	text-align: center;
  	height: 60px;
  }
  
  .center-preview .el-tabs /deep/ .el-tabs__content {
  	padding: 10px;
  	background: #fff;
  	width: 100%;
  }
  .center-preview .el-tabs /deep/ .el-tabs__content .el-tab-pane {
  }
  
  .center-preview-pv .el-form-item /deep/ .el-form-item__label {
  	padding: 0 10px 0 0;
  	color: #000;
  	font-weight: 500;
  	width: 200px;
  	font-size: 14px;
  	line-height: 40px;
  	text-align: right;
  }
  
  .center-preview-pv .el-form-item .el-form-item__content {
    margin-left: 200px;
  }
  
  .center-preview-pv .el-input /deep/ .el-input__inner {
  	border: 1px solid #E2E3E5;
  	border-radius: 0;
  	padding: 0 12px;
  	box-shadow: none;
  	outline: none;
  	color: #000;
  	width: 500px;
  	font-size: 14px;
  	height: 40px;
  }
  
  .center-preview-pv .el-select /deep/ .el-input__inner {
  	border: 1px solid #E2E3E5;
  	border-radius: 0;
  	padding: 0 12px;
  	box-shadow: none;
  	outline: none;
  	color: #000;
  	width: 500px;
  	font-size: 14px;
  	height: 40px;
  }
  
  .center-preview-pv .el-date-editor /deep/ .el-input__inner {
  	border: 1px solid #E2E3E5;
  	border-radius: 0;
  	padding: 0 10px 0 30px;
  	box-shadow: none;
  	outline: none;
  	color: #000;
  	width: 500px;
  	font-size: 14px;
  	height: 40px;
  }
  
  .center-preview-pv /deep/ .avatar-uploader-icon {
  	border: 1px solid #E2E3E5;
  	cursor: pointer;
  	border-radius: 0;
  	color: #000;
  	width: 200px;
  	font-size: 32px;
  	line-height: 60px;
  	text-align: center;
  	height: 60px;
  }
  
  .center-preview-pv .el-form-item.balance /deep/ .el-input__inner {
  	border: 1px solid #E2E3E5;
  	border-radius: 0;
  	padding: 0 12px;
  	box-shadow: none;
  	outline: none;
  	color: #000;
  	display: inline-block;
  	width: 390px;
  	font-size: 14px;
  	height: 40px;
  }
</style>
