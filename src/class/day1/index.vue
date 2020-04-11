<template>
    <div>
        day1：
        <label for="">{{formObj}}</label>
        <f-form :model="formObj">
            <f-form-item title="账号">
                <f-input v-model="formObj.username" />
            </f-form-item>
            <f-form-item title="密码">
                <f-input v-model="formObj.password" type="password" />
            </f-form-item>
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
        }
    }
</script>

<style scoped>

</style>