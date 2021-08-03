<template>
  <a-form layout='inline' :form="form">
    <a-form-item label='Username'>
      <a-input
              v-decorator="[
            'username',
            {
              rules: [{ required: true, message: 'Username is required!' }],
            }
          ]"
      />
    </a-form-item>
  </a-form>
</template>

<script>
export default {
  props: ['username'],
  created() {
    this.form = this.$form.createForm(this, {
      name: 'global_state',
      onFieldsChange: (_, changedFields) => {
        // eslint-disable-next-line no-debugger
        debugger
        this.$emit('change', changedFields);
      },
      mapPropsToFields: () => {
        // eslint-disable-next-line no-debugger
        debugger
        return {
          username: this.$form.createFormField({
            ...this.username,
            value: this.username.value,
          }),
        };
      },
      onValuesChange(_, values) {
        console.log(values);
      },
    });
  },
  watch: {
    username() {
      this.form.updateFields({
        username: this.$form.createFormField({
          ...this.username,
          value: this.username.value,
        }),
      });
    },
  },
}
</script>
