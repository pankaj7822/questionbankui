<template>
  <v-card>
    <v-card-title>
      IOE Old Question Database For Electronics and Communication Engineering
      <v-spacer></v-spacer>
      <v-select
        v-model="search"
        :items="courses"
        label="Search By Course Title"
      ></v-select>
    </v-card-title>
    <v-data-table :headers="headers" :items="papers" :search="search">
      <template #item.link="{ value }">
        <a target="_blank" :href="value">
          {{ value }}
        </a>
      </template>
    </v-data-table>
  </v-card>
</template>

<script>
export default {
  data() {
    return {
      search: "",
      courses: [],
      headers: [
        { text: "Course Code", value: "course_code" },
        { text: "Course Title", value: "course_title" },
        { text: "Semester", value: "semester" },
        { text: "Department", value: "department" },
        { text: "Program", value: "program" },
        { text: "Course Type", value: "course_type" },
        { text: "Exam Year", value: "year" },
        { text: "Exam Type", value: "type" },
        { text: "Paper Link", value: "link", sortable: false }
      ],
      papers: []
    };
  },
  created() {
    this.$axios
      .get("https://questionbankioe.herokuapp.com/getpapers")
      .then(response => (this.papers = response.data.paper_list));
    this.$axios
      .get("https://questionbankioe.herokuapp.com/getcourses")
      .then(response => (this.courses = response.data.course_list));
  },
  methods: {}
};
</script>
