<template>
    <div>
        day1：
        <label for="">{{formObj}}</label>
        <f-form ref="loginForm" :model="formObj" :rules="rules">
            <f-form-item title="账号" prop="username">
                <f-input v-model="formObj.username" />
            </f-form-item>
            <f-form-item title="密码" prop="password">
                <f-input v-model="formObj.password" type="password" />
            </f-form-item>
            <button @click="login">登录</button>
        </f-form>
    </div>
</template>

<script>
    import FInput from './FInput'
    import FFormItem from './FFormItem'
    import FForm from './FForm'
    export default {
        data() {
            return {
                inputVal: '',
                pas: '',
                formObj: {
                    username: 'cpf',
                    password: ''
                },
                rules: {
                    username: [{required:true, message:'用户名必填'}],
                    password: [{required:true, message:'密码必填'}]
                }
            }
        },
        components: {
            FInput,
            FFormItem,
            FForm
        },
        methods: {
            login() {
                this.$refs.loginForm.validate((isValid)=>{
                    if(isValid){
                        alert('登录========')
                    }else{
                        alert('校验有问题')
                    }
                })
            }
        }
    }
</script>

<style scoped>

</style>