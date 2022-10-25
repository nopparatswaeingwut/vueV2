<template>
 <form action="#" @submit.prevent="onSubmit">
    <p v-if="errorsPresent" class="error">กรอกข้อมูลให้ครบถ้วน</p>
    <div class="ui labeled input fluid">
      <div class="ui label">
        <i class=""></i>ชื่อ
      </div>
      <input type="text" placeholder="" v-model="task.task1" />
    </div>
    <div class="ui labeled input fluid">
      <div class="ui label">
   <i class=""></i> ที่อยู่
      </div>
      <input type="text" placeholder="" v-model="task.task2" />
    </div>
    <div class="ui labeled input fluid">
      <div class="ui label">
        <i class=""></i>อายุ
      </div>
      <input type="number" placeholder="" v-model="task.task3" />
    </div>
    <div class="ui labeled input fluid">
      <div class="ui label">
        <i class=""></i>งานอดิเรก
      </div>
      <input type="text" placeholder="" v-model="task.task4" />
    </div>
    <button class="positive ui button">ตกลง</button>
  </form>
</template>
<script>
export default {
  name: 'task-form',
  props: {
    task: {
      type: Object,
      required: false,
      default: () => {
        return {
          task1: '',
          task2: '',
          task3: '',
          task4: '',
        };
      }
    }
  },
  data() {
    return {
      errorsPresent: false
    };
  },
  methods: {
    onSubmit: function() {
      if (this.task.task1 === '' || this.task.task2 === '') 
      {
        this.errorsPresent = true;
      }
      if (this.task.task3 === '' || this.task.task4 === '') 
      {
        this.errorsPresent = true;
      } 
      else {
    
        this.$emit('createOrUpdate', this.task);
      }
    }
  }
};
</script>
<style scoped>
.error {
  color: red;
}
</style>