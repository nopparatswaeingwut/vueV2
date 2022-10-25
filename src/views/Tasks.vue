<template>
  <div >
    <h1>#รายชื่อ</h1>
    <flash-message></flash-message>
    <div v-if="tasks.length > 0">
    <table id="tasks" class="ui celled compact table ">
      <thead>
        <tr>
            <th><i class="tasks icon "></i>ชื่อ</th>
            <th><i class=""></i>รายละเอียด</th>
            <th><i class="search icon "></i></th>
            <th><i class="edit icon"></i></th>
            <th><i class="trash icon"></i></th>
        </tr>
      </thead>
      <tr v-for="(task, i) in tasks" :key="i">
        <td>{{ task.name }}</td>
        <td>{{ task.details }}</td>
  
        <td width="75" class="center aligned ">
          <router-link :to="{ name: 'show', params: { id: task._id }}">ดูรายละเอียด</router-link>
        </td>
        <td width="75" class="center aligned">
          <router-link :to="{ name: 'edit', params: { id: task._id }}">แก้ไข</router-link>
        </td>
        <td width="75" class="center aligned" @click.prevent="onDestroy(task._id)">
          <a :href="`/tasks/${task._id}`">ลบ</a>
        </td>
      </tr>
    </table>
    </div>
    <div v-else>
        ไม่มีรายชื่อในรายการ
    </div>
  </div>
</template>
<script>
import { api } from '../helpers/Helpers';
export default {
  name: 'tasks',
  data() {
    return {
      tasks: []
    };
  },
  methods: {
    async onDestroy(id) {
      const sure = window.confirm('คุณต้องการลบรายการนี้หรือไม่ ?');
      if (!sure) return;
      await api.deletetask(id);
      this.flash('ลบรายการที่คุณเลือกเรียบร้อย', 'success');
      const newtasks = this.tasks.filter(task => task._id !== id);
      this.tasks = newtasks;
    }
  },
  async mounted() {
    this.tasks = await api.gettasks();
  }
};
</script>
<style>

/* a2{
  color: rgba(15, 100, 228, 0.815);
}
a1{
  color: rgb(236, 130, 9);
}
a3{
  color: rgba(228, 21, 49, 0.733);
} */
</style>