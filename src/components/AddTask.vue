<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>Task</label>
      <input type="text" v-model="text" name="text" placeholder="Add task" />
    </div>

    <div class="form-control">
      <label>Day & Time</label>
      <input
        type="text"
        v-model="day"
        name="day"
        placeholder="Add Day & Time"
      />
    </div>

    <div class="form-control form-control-check">
      <label>Set Reminder</label>
      <input
        type="checkbox"
        v-model="reminder"
        name="reminder"
        class="checkbox"
      />
    </div>

    <input type="submit" value="Save Task" class="btn btn-block" />
  </form>
</template>

<script>
export default {
  name: "AddTask",

  data() {
    return {
      text: "",
      day: "",
      reminder: false,
    };
  },

  methods: {
    onSubmit(e) {
      e.preventDefault();

      if (!this.text) {
        alert("Please add a task");
        return;
      }

      const newTask = {
        id: Math.floor(Math.random() * 100000),
        text: this.text,
        day: this.day,
        reminder: this.reminder,
      };
      this.$emit("add-task", newTask);

      this.text = "";
      this.day = "";
      this.reminder = false;
    },
  },
};
</script>

<style scoped>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.add-form {
  margin-bottom: 40px;
  font-weight: bold;
}

.form-control label {
  display: block;
  margin-bottom: 10px;
}

.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}

.form-control-check {
  display: flex;
  align-items: center;
  font-weight: bold;
  margin-top: 10px;
  margin-right: 91%;
}

.form-control-check label {
  flex: 1;
  height: 20px;
}

.btn {
  color: white;
  font-size: 100%;
  background: black;
  padding: 10px;
  width: 100%;
  border-radius: 2px;
  border-color: black;
  margin-top: 30px;
}
</style>
