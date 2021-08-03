<template>
  <div id="app">
    <img src="./assets/logo.png">
    <div>
      <p>
        If Element is successfully added to this project, you'll see an
        <code v-text="'<el-button>'"></code>
        below
      </p>
      <el-button>el-button</el-button>
      <a-button type="primary">Ant Primary</a-button>
    </div>

    <div>
      <div id="components-form-demo-global-state">
        <customized-form :username="fields.username" @change="handleFormChange"/>
        <pre class="language-bash">
         {{ JSON.stringify(fields, null, 2) }}
        </pre>
      </div>

    </div>
  </div>
</template>

<script>
import CustomizedForm from './components/CustomizedForm.vue'

export default {
  name: 'app',
  components: {
    CustomizedForm
  },
  data() {
    return {
      fields: {
        username: {
          value: 'benjycui',
        },
      },
    }
  },
  methods: {
    handleFormChange(changedFields) {
      console.log('changedFields', changedFields);
      this.fields = { ...this.fields, ...changedFields };
    },
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#components-form-demo-global-state .language-bash {
  max-width: 400px;
  border-radius: 6px;
  margin-top: 24px;
}
</style>
