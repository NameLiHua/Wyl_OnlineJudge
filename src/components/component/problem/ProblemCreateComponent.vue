<template>
    <div class="button-container">
        
        <el-button-group class="button-group">
            
          <el-button class="useless"></el-button>
          <el-button @click="validateLogon" class="button-gp second-button"  style="width: 100%; height: 50%"><el-icon><Plus /></el-icon> &ensp; 新建题目</el-button>
          <el-button class="button-gp first-button" style="width: 100%; height: 50%">按钮2</el-button>
          
          <el-button class="button-gp third-button" style="width: 100%; height: 50%">按钮3</el-button>
        </el-button-group>
      </div>




  <el-dialog v-model="centerDialogVisible" title="用户未登录" width="30%" center>
    <span>
      新建题目功能必须登录后才能使用
    </span>
    <template #footer>
      <span class="dialog-footer">
        <el-button @click="centerDialogVisible = false">取消</el-button>
        <el-button style="color:white" type="primary" @click="toLogin">
          登录
        </el-button>
      </span>
    </template>
  </el-dialog>
      
</template>

<script>
import { Plus } from '@element-plus/icons-vue'
import router from '@/router/router'
export default {
  components: {
    Plus
  },
  data(){
    return {
        centerDialogVisible:false
    }
  },
  methods:{
    validateLogon(){
        if(this.$store.state.userInfo.userloginstate === false){
            this.centerDialogVisible = true
            return
        }
        router.push({name:'createproblem'})
    },
    toLogin(){
        this.centerDialogVisible = false
        router.push({name:'userlogin'})
    }
    
  },
  setup(){
    
  }
}
</script>

<style scoped>
.first-button{
}

.button-container{
    position: relative;
    left:20px
}
.useless{
    position: relative;
    top: -200px;
}
.button-group{
    position: relative;
    top:-22px
}
</style>