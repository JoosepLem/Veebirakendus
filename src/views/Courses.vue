
<template>
  <div>
    <h1>Courses</h1>
    <div v-for="course in courses" :key="course.id">
      <Course :course="course" />
    </div>
  </div>
</template>

<script>
import Course from "@/components/course.vue";

export default {
  components: {
    Course,
  },
  data() {
    return {
      courses: [],
    };
  },
  methods: {
    fetchRecords() {
      fetch(`http://localhost:3000/api/courses`)
        .then((response) => response.json())
        .then((data) => (this.courses = data))
        .catch((err) => console.log(err.message));
    },
  },
  mounted() {
    this.fetchRecords();
    console.log("mounted");
  },
};
</script>

<style scoped>

h3 {
  text-align: center;
  color: rgb(8, 110, 110);
}

table {
  background: gray;
  border: 2px solid lightgray;
  border-radius: 5px;
  width: 85%;
  margin: auto;
}

td {
  font-size: 15px;
  padding: 15px 20px;
  background: rgb(185, 138, 230);
}
</style>
