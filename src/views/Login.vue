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
                                  @click="onSubmit"
                                >第三方登录</el-button>
                            </el-form-item>
                        </el-form>
                    </el-card>
                </div>
            </el-col>
        </el-row>
    </div>
</template>

<script setup>
import { reactive } from 'vue'
import { UserFilled, Hide, Plus } from "@element-plus/icons-vue"
// do not use same name with ref
const form = reactive({
  name: '',
  password:''
})

const onSubmit = () => {
  console.log('submit!')
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