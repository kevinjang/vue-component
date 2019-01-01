<template>
  <div>
    <p v-if="label">{{label}}</p>
    <div>
      <slot></slot>
      <p v-if="validateStatus=='error'" class="error">{{errorMessage}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "KFormItem",
  inject: ["form"],
  props: {
    label: {
      type: String
    },
    prop: {
      type: String
    }
  },
  data() {
    return {
      validateStatus: "",
      errorMessage: ""
    };
  },
  methods: {
    getRules() {
      const rule = this.form.rules[this.prop];
      //   console.log(rule);
      return rule;
    }
  },
  created() {
    this.$bus.$on("KFormItem", value => {
      //   console.log("emit received");
      const rule = this.getRules();
      //   console.log(rule);
      console.log(value.name);
      if (value.name != this.prop) {
      } else {
        //   console.log('value.valu:'+value.valu);
        if (rule.required && !value.valu) {
          this.validateStatus = "error";
          this.errorMessage = rule.message;
        } else {
          console.log("value.valu:" + value.valu);
          this.validateStatus = "validating";
        }
      }
    });
  }
};
</script>

<style>
p.error {
  color: red;
}
</style>
