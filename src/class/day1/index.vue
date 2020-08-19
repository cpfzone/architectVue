<template>
  <div>
    day1：
    <label for>{{formObj}}</label>
    <f-form ref="loginForm" :model="formObj" :rules="rules">
      <f-form-item title="账号" prop="username">
        <f-input v-model="formObj.username" />
      </f-form-item>
      <f-form-item title="密码" prop="password">
        <f-input v-model="formObj.password" type="password" />
      </f-form-item>
      <button @click="login">登录</button>
    </f-form>
    <c-form ref="loginForm1" :model="formObj" :rules="rules">
        <c-form-item title="账号" prop="username">
            <c-input v-model="formObj.username" />
        </c-form-item>
        <c-form-item title="密码" prop="password">
            <c-input v-model="formObj.password" type="password" />
        </c-form-item>
        <button @click="login1">登录</button>
    </c-form>
  </div>
</template>

<script>
import FInput from "./FInput";
import CInput from "./CInput"; 
import FFormItem from "./FFormItem";
import FForm from "./FForm";
import CForm from "./CForm";
import CFormItem from "./CFormItem";
export default {
  data() {
    return {
      inputVal: "",
      pas: "",
      formObj: {
        username: "cpf",
        password: ""
      },
      rules: {
        username: [{ required: true, message: "用户名必填" }],
        password: [{ required: true, message: "密码必填" }]
      }
    };
  },
  components: {
    FInput,
    FFormItem,
    FForm,
    CInput,
    CForm,
    CFormItem
  },
  methods: {
    login() {
      this.$refs.loginForm.validate(isValid => {
        if (isValid) {
          alert("登录========");
        } else {
          alert("校验有问题");
        }
      });
    },
    login1() {
         this.$refs.loginForm1.validate(isValid => {
        if (isValid) {
          alert("登录1========");
        } else {
          alert("校验1有问题");
        }
      });
    }
  }
};
</script>

<style scoped>
</style>