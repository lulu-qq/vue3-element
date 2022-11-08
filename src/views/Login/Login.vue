<template>
    <div class="box">
        <el-row>
            <el-col :span="24">
                <div class="grid-content ep-bg-purple-dark" >
                    <el-card class="box-card" >
                        <template #header>
                        <div class="card-header">
                            <span>系统登陆</span>
                            <el-icon class="icons"><Plus /></el-icon>
                        </div>
                        </template>
                        <el-form :model="form">
                            <el-form-item>
                                <el-input 
                                    v-model="form.name"  
                                    :prefix-icon="UserFilled"
                                />
                            </el-form-item>
                            <el-form-item>
                                <el-input 
                                    type="password" 
                                    v-model="form.password"  
                                    :prefix-icon="Hide"
                                    show-password
                                    />
                            </el-form-item>
                            <el-form-item>
                                <el-button 
                                  type="primary" 
                                  @click="onSubmit"
                                  class="subButton"
                                >登录</el-button>
                            
                            </el-form-item>
                            <el-form-item
                                class="add"
                            >
                                <el-button 
                                  type="primary" 
                                  @click="onThreeSubmit"
                                >第三方登录</el-button>
                            </el-form-item>
                        </el-form>
                    </el-card>
                </div>
                <!-- 第三方登录框 -->
                <div>
                    <el-dialog
                        v-model="dialogVisible"
                        title="第三方登录"
                        width="30%"
                    >
                        <span>本地不能模拟，请结合自己业务进行模拟！！！</span>
                        <template #footer>
                        <span class="dialog-footer">
                            <el-button type="primary" @click="dialogVisible = false">
                            Confirm
                            </el-button>
                        </span>
                        </template>
                    </el-dialog>
                </div>
            </el-col>
        </el-row>
    </div>
</template>

<script setup>
import { reactive, ref } from 'vue'
import { UserFilled, Hide, Plus } from "@element-plus/icons-vue"
import { useRouter } from 'vue-router'
// do not use same name with ref
const history = useRouter()
const form = reactive({
  name: '',
  password:''
})
const dialogVisible = ref(false)
const onSubmit = () => {
  console.log('submit!')
  history.push('/')
}

const onThreeSubmit  = ()=>{
    dialogVisible.value = true
}
</script>


<style lang="scss" scoped>
.box{
    height:100vh;
    width: 100%;
    background:skyblue;
    .card-header{
        display: flex;
        align-items: center;
        justify-content: center;
        position:relative;
        .icons{
            position:absolute !important;
            right:0;
            top:-2px;
        }
    }
    .grid-content{
        display: flex;
        justify-content: center;
    }
    .el-row{
        height:100%;
        align-items: center;
        justify-content: center;
        .box-card{
            width:520px;
        }
    }
    .subButton{
        width: 100%;
    } 
}
</style>
<style lang="scss">
  .add{
         .el-form-item__content{
            justify-content: end !important;
        }
    } 
    
</style>