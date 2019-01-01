<template>
  <div>
    <input type="text" :value="inputValue" @input="handleInput" @blur="handleBlur">
  </div>
</template>

<script>
export default {
  name: "KInput",
  props: {
    value: {
      type: String,
      required: true
    },
    name:{
        type:String,
        required:true
    }
  },
  data() {
    return {
      inputValue: this.value
    };
  },
  methods: {
    handleInput(e) {
        // 变量由祖父定义，发生修改需要由祖父组件进行修改
        const valu = e.target.value;
        this.inputValue = valu;

        this.$bus.$emit('KFormItem',valu);
    },
    handleBlur(e) {
        // console.log(e.target.value)
        const valu = e.target.value;
        this.inputValue = valu;

        this.$bus.$emit('KFormItem',{
            valu,
            name:this.name
        });
    }
  }
};
</script>

<style>
</style>
