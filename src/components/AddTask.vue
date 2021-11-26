<template>
    <form @submit="onSubmit" class="add-form">
        <div class="form-control">
            <label for="">Task</label>
            <input type="text" v-model="text" name="text" placeholder="Task text">
        </div>
        <div class="form-control">
            <label for="">Date & Time</label>
            <input type="text" v-model="time" name="time" placeholder="Task Date & Time">
        </div>
        <div class="form-control form-control-check">
            <label>Reminder</label>
            <input type="checkbox" v-model="reminder" name="reminder" value="Save Task">
        </div>
        <input type="submit" value="Save Task" class="btn btn-block">
    </form>
</template>

<script>
export default {
    name: 'AddTask',
    data() {
        return {
            text: '',
            time: '',
            reminder: false
        }
    },
    methods: {
        onSubmit(e) {
            e.preventDefault()

            if(!this.text) {
                alert('Please enter text')
                return
            }
            const newTask = {
                id: Math.floor(Math.random() * 1000000),
                text: this.text,
                time: this.time,
                reminder: this.reminder
            }

            this.$emit('add-task', newTask)

            console.log(newTask)
            this.text = ''
            this.time = ''
            this.reminder = false
        }
    }
}
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
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
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>