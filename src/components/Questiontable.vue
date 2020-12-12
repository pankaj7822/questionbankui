<template>
  <v-card>
    <v-card-title>
      IOE Old Question Database For Electronics and Communication Engineering
      <v-spacer></v-spacer>
      <v-text-field
        v-model="search"
        append-icon="mdi-magnify"
        label="Search"
        single-line
        hide-details
      ></v-text-field>
    </v-card-title>
    <v-data-table
      :headers="headers"
      :items="papers"
      :search="search"
    ></v-data-table>
  </v-card>
</template>

<script>
export default {
  data() {
    return {
      search: "",
      headers: [
        {
          text: "Exam Year",
          align: "start",
          value: "year"
        },
        { text: "Exam Type", value: "type" },
        { text: "Paper Link", value: "link", sortable: false }
      ],
      papers: []
    };
  },
  created() {
    axios
      .get("http://127.0.0.1:8000/getpapers")
      .then(response => (this.papers = response.data));
  }
};
</script>
