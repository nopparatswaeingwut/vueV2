<template>
  <div>
    <h1>#รายละเอียด</h1>
    <flash-message></flash-message>
    <div class="ui labeled input fluid">
      <div class="ui label ">
      <i class=""></i>  ชื่อ
      </div>
      <input type="text" readonly  :value="task.name"/>
    </div>
     <div class="ui labeled input fluid">
      <div class="ui label">
        <i class=""></i> รายละเอียด
      </div>
      <input type="text" readonly  :value="task.details"/>
    </div>
    <div class="ui labeled input fluid">
      <div class="ui label ">
      <i class=" "></i>  อายุ
      </div>
      <input type="number" readonly  :value="task.age"/>
    </div>
    <div class="ui labeled input fluid">
      <div class="ui label ">   
      <i class=""></i>  งานอดิเรก
      </div>
      <input type="text" readonly  :value="task.hobby"/>
    </div>
    <div class="actions">
      <router-link :to="{ name: 'edit', params: { id: this.$route.params.id }}">
        แก้ไข
      </router-link>
    </div>
  </div>
</template>

<script>
import { api } from '../helpers/Helpers';
export default {
  name: 'show',
  data() {
    return {
      task: ''
    };
  },
  async mounted() {
    this.task = await api.gettask(this.$route.params.id);
  }
};
</script>
<style scoped>
.actions a {
  display: block;
  text-decoration: underline;
  margin: 20px 10px;
}
</style>