<template>
  <form @submit="onSubmit">
    <div class="form-control">
      <label>Text</label>
      <input type="text" name="text" v-model="text" placeholder="Add text" />
    </div>
    <div class="form-control">
      <label>Day</label>
      <input type="text" name="day" v-model="day" placeholder="Add day" />
    </div>
    <div class="form-control">
      <label>Reminder</label>
      <input type="checkbox" name="reminder" v-model="reminder" />
    </div>
    <input type="submit" value="Save Task" class="btn btn-block" />
  </form>
</template>

<script>
export default {
  name: 'AddTask',
  data() {
    return {
      text: '',
      day: '',
      reminder: false,
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();
      if (this.text !== '') {
        const newTask = {
          id: Math.floor(Math.random() * 1000000),
          text: this.text,
          day: this.day,
          reminder: this.reminder,
        };

        this.$emit('add-task', newTask);
        this.text = '';
        this.day = '';
        this.reminder = false;
      } else {
        alert('Please enter text for task');
      }
    },
  },
};
</script>

<style scoped>
form {
  margin-bottom: 2rem;
}
.form-control {
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: large;
  margin: 1rem 0;
}
label {
  padding: 2px 4px;
  display: block;
  width: 100%;
  text-align: left;
}

input {
  padding: 0.5rem;
  width: 100%;
  display: block;
  outline: none;
  height: 2rem;
}
</style>
