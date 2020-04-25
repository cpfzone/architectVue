<template>
    <div>
        <label v-if="title">{{ title }}</label>
        <slot />
        <p >{{ message }}</p>
    </div>
</template>

<script>
    import Schema from 'async-validator'
    export default {
        name: 'FFormItem',
        inject: ['form'],
        props: {
            title: String,
            prop: String
        },
        data() {
            return{
                messageShow: false,
                message: ''
            }
        },
        mounted() {
          this.$on('validate', this.validate)  
        },
        methods: {
            validate() {
                console.log('进行校验。。。。',this.prop)
                // 1. 拿到校验规则 
                const rule = this.form.rules[this.prop]
                // 2. 拿到校验的值
                const value = this.form.model[this.prop]
                console.log('rule =====', rule, "value ==========", value)
                // 3. 执行校验
                const desc = {
                    [this.prop]: rule
                }
                const schema = new Schema(desc);
               return schema.validate({ [this.prop]: value }, err => {
                    if (err) {
                        this.message = err[0].message
                    } else {
                        this.message = ''
                    }
                })
            }
        }
    }
</script>

<style scoped>

</style>