<template>
  <div>
    <h1>#เพื่มรายชื่อ</h1>
    <task-form @createOrUpdate="createOrUpdate"></task-form>
  </div>
</template>
<script>
import taskForm from '../components/TaskForm.vue';
import { api } from '../helpers/Helpers';
export default {
  name: 'new-task',
  components: {
    'task-form': taskForm
  },
  methods: {
    createOrUpdate: async function(task) {
      const res = await api.createtask(task);
      this.flash('เพิ่มรายชื่อสำเร็จ', 'success');
      this.$router.push(`/tasks/${res._id}`);
    }
  }
};
</script>