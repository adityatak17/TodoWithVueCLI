<template>
    <div v-show="todotaskslist.length">
        <ul>
            <li v-for=" (task,index) in todotaskslist" :key="index">
                <p>Title:   {{task.title}}</p>
                <p>Description: {{task.description}}</p>
                <div class="form-buttons">
                    <button class="button" @click="moveToOngoing(task,index,instanceNumber)">Move to Ongoing Tasks</button>
                    <button class="button" @click="moveToCompleted(task,index,instanceNumber)">Move to Completed Tasks</button>
                    <button class="button" @click="moveToDeleted(task,index,instanceNumber)">Delete This Task</button>
                </div>
                <br>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
  name: "TodoComponent",
  props: {
    todotaskslist: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      instanceNumber: 0,
    };
  },
  methods: {
    moveToOngoing(task, index, instanceNumber) {
      this.$emit("move-to-ongoing", task, index, instanceNumber);
    },
    moveToCompleted(task, index, instanceNumber) {
      this.$emit("move-to-completed", task, index, instanceNumber);
    },
    moveToDeleted(task, index, instanceNumber) {
      this.$emit("move-to-deleted", task, index, instanceNumber);
    },
  },
};
</script>