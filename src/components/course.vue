<template>
    <tr class="course">
      <td><b>Course name:</b> <br> {{ course.coursename }}</td>
      <td>
        <b>Code:</b> <br>
        <a :href="`/acourse/${course.id}`">{{ course.coursecode }}</a>
      </td>
      <td><b>ECTS:</b> <br> {{ course.courseects}}</td>
      <td><b>Max No. of Students:</b> <br> {{ course.studentsnumbers }}</td>
      <td><b>No. of Groups:</b> <br> {{ course.groupsnumbers }}</td>
    </tr>
  </template>
  
  <script>
  export default {
    props: {
      course: {
        type: Object,
        required: true,
      },
    },
  };
  </script>
  
  <style scoped>
  .course {
    background-color: purple;
    border: 1px solid lightgray;
    padding: 10px;
    text-align: left;
  }
  
  .course td {
    font-size: 15px;
    margin-bottom: 5px;
    padding: 15px 50px;
  }
  
  .course td a {
    color: blue;
    text-decoration: underline;
    cursor: pointer;
  }
  
  .course {
    background: rgb(233, 180, 253);
    margin-bottom: 30px;
    padding: 10px 20px;
    margin: auto;
    width: 85%;
    display: flex;
  }
  </style>
  