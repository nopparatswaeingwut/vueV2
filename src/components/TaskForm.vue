<template>
 <form action="#" @submit.prevent="onSubmit">
    <p v-if="errorsPresent" class="error">กรอกข้อมูลให้ครบถ้วน</p>
    <div class="ui labeled input fluid">
      <div class="ui label">
        <i class=""></i>ชื่อ
      </div>
      <input type="text" placeholder="" v-model="task.Name" />
    </div>
    <div class="ui labeled input fluid">
      <div class="ui label">
   <i class=""></i> รายละเอียด
      </div>
      <input type="text" placeholder="" v-model="task.details" />
    </div>
    <div class="ui labeled input fluid">
      <div class="ui label">
        <i class=""></i>อายุ
      </div>
      <input type="number" placeholder="" v-model="task.age" />
    </div>
    <div class="ui labeled input fluid">
      <div class="ui label">
        <i class=""></i>งานอดิเรก
      </div>
      <input type="text" placeholder="" v-model="task.hobby" />
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
          Name: '',
          details: '',
          age: '',
          hobby: '',
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
      if (this.task.Name === '' || this.task.details === '') 
      {
        this.errorsPresent = true;
      }
      if (this.task.age === '' || this.task.hobby === '') 
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