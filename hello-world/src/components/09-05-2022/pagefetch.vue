<template>
  <div>
    <b-pagination
      v-model="currentPage"
      :total-rows="rows"
      :per-page="perPage"
    ></b-pagination>
    <b-tabs>
      <b-tab title="Tab 1" @click="func1()" active>
        <b-table
          :items="res"
          :fields="fields"
          :per-page="perPage1"
          :current-page="currentPage"
        ></b-table>
      </b-tab>
      <b-tab title="Tab 2" @click="func2()" active>
        <b-table
          :items="result"
          :fields="fields"
          :per-page="perPage2"
          :current-page="currentPage"
        ></b-table>
      </b-tab>
    </b-tabs>
  </div>
</template>

<script>
export default {
  name: "FEtch",
  data() {
    return {
      perPage1: 3,
      perPage2: 5,
      currentPage: 1,
      res: " ",
      result: " ",
      array: [1, 2, 3],
    };
  },
  methods: {
    async func1() {
      let response = await fetch("https://jsonplaceholder.typicode.com/todos");
      this.res = await response.json();
      return this.res;
    },
    async func2() {
      let response = await fetch(
        "http://universities.hipolabs.com/search?country="
      );
      this.result = await response.json();
    },
  },
  computed: {
    rows() {
      //return this.res.length;
      return this.result.length;
    },
  },
};
</script>

<style></style>
