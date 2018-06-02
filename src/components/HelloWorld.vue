<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Vue 登录Demo</h2>
  <!-- <el-row :gutter="20">
    <el-col :span="12" :offset="6">
        <div class="grid-content bg-purple">
          <el-input v-model="username" placeholder="请输入内容"></el-input>
        </div>
      </el-col>
  </el-row>
  <el-row :gutter="20">
    <el-col :span="12" :offset="6">
        <div class="grid-content bg-purple">
          <el-input v-model="password" placeholder="请输入内容"></el-input>
        </div>
      </el-col>
  </el-row> -->
<el-form :label-position="labelPosition" label-width="80px" :model="formLabelAlign">
  <el-row :gutter="20">
      <el-col :span="12" :offset="6">
          <div class="grid-content bg-purple">
            <el-form-item label="账号：">
            <el-input v-model="formLabelAlign.name"></el-input>
          </el-form-item>
          </div>
        </el-col>
    </el-row>
    <el-row :gutter="20">
      <el-col :span="12" :offset="6">
          <div class="grid-content bg-purple">
            <el-form-item label="密码：">
            <el-input v-model="formLabelAlign.pass"></el-input>
          </el-form-item>
          </div>
        </el-col>
    </el-row>
  </el-form>
</el-form>
  </el-row>
     <el-button v-on:click="getTest">登录</el-button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      labelPosition: 'right',
        formLabelAlign: {
          name: '',
          pass: ''
        }
    }
  },
  methods:{

    getTest(){ //方法
      console.log(this.formLabelAlign);
      let name = this.formLabelAlign.name;
      let pass = this.formLabelAlign.pass ;
      if(""!=name&&""!=pass){
        this.$http.post("login",{
          "username": this.formLabelAlign.name,
          "password": this.formLabelAlign.pass,
        }).then((response) => {
            console.log(response.data)
            if(response.data.flag==true){
              alert("登录成功")
            }else{
              alert("登录失败")
            }
        })
      }
      
    }

}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
