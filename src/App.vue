<template>
  <div>
    <k-form v-model="form" :rules="rules">
      <k-form-item label="用户名" prop="name">
        <k-input :value="form.name" name="name"></k-input>
      </k-form-item>
      <k-form-item label="年龄" prop="age">
        <k-input :value="form.age" name="age"></k-input>
      </k-form-item>
    </k-form>
  </div>
</template>

<script>
import KForm from "./components/Form";
import KFormItem from "./components/FormItem";
import KInput from "./components/Input";

export default {
  name: "app",
  components: {
    KForm,
    KFormItem,
    KInput
  },
  data() {
    return {
      form: {
        name: "Damien Crosse",
        age: "36"
      },
      rules: {
        name: {
          required: true,
          message: "用户名必填"
        },
        age: {
          required: true,
          message: "年龄必填"
        }
      }
    };
  }
};
</script>

<style>
</style>
