<template>
<div class="ACourse">
  <h1>Course Details</h1>
  <div>
    <strong>Course Name:</strong> {{ courseData.coursename }}
  </div>
  <div><strong>Code:</strong> {{ courseData.courseCode }}
  </div>
  <div><strong>ECTS:</strong> {{courseData.courseects }}</div>
  <div><strong>Max No. of Students:</strong> {{ courseData.studentsnumbers }}
  <input v-model="newStudents" type="number" />
  </div>
  <div><strong>No. of Groups:</strong> {{ courseData.groupsnumbers }}
    <input v-model="newGroups" type="number" /></div>
  <div><strong>Description:</strong> {{ courseData.description }}
    <textarea v-model="newDescription"></textarea></div>

  <button @click="updateCourseData">Update Data</button>
</div>
</template>


<script>
export default {
  name: "ACourse",
  data() {
    return {
      courseData: {
        coursename:"",
        coursecode:"",
        courseects:"",
        studentsnumbers:"",
        groupsnumbers:"",
        description:"",
        },
        newStudents: "",
        newGroups:"",
        newDescription:"",
    };
  },
  methods: {
    async fetchCourseData(courseId) {
      try {
        const response = await fetch(`http://localhost:3000/api/courses/${courseId}`);
        const data = await response.json();
        this.courseData = data;
      } catch (error) {
        console.error(error.message);
      }
    },
    async updateCourseData() {
      try{
        const courseId = this.$route.params.id;
        const response = await fetch(`http://localhost:3000/api/courses/${courseId}`, {
          method: 'PUT',
          headers: {
            'Content-Type': 'application/json'
          },
          body: JSON.stringify({
            studentsnumbers: this.newStudents,
            groupsnumbers: this.newGroups,
            description: this.newDescription,
          }),
        });
        if (response.ok) {
          this.$router.push('/courses')
        }
      } catch (error) {
        console.error(error.message);
      }
    }
  },
  mounted() {
    const courseId = this.$route.params.id;
    this.fetchCourseData(courseId);
  } 
};
</script>

<style scoped>
.ACourse {
  text-align: center;
  margin: auto;
  padding: 20px;
  border: 1px solid black;
  border-radius: 5px;
  background-color: bisque;
}

h1 {
  color: black
}

div {
  margin-bottom: 10px;
}

button {
  margin-top: 5px;
  padding: 8px;
  border: 1px;
  border-radius: 4px;
}
</style>