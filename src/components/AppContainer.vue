<template>
  <div class="container">
      <topNav @addForm="addForm"/>
      <table class="table">
          <tr class="headings-row">
              <th class="heading" v-for="heading in logHeadings" :key="heading">{{ heading }}</th>
          </tr>
          <div v-for="months in mockData" :key="months">
              <tr class="row" v-for="logs in months" :key="logs">
                  <td class="cell">{{ logs.date }}</td>
                  <td class="cell">{{ logs.daytodate }}</td>
                  <div class="cell">
                      <td class="yes" v-if="logs.attended">yes</td>
                      <td class="no" v-if="!logs.attended">no</td>
                  </div>
                  <td class="cell">{{ logs.notes }}</td>
                </tr>
          </div>
      </table>
      <div class="dropdown" v-if="displayDropdown">dropdown</div>
  </div>
</template>

<script>
import topNav from "./topNav.vue";

//import mock data
import mockData from "../mockData/mockData.json";

export default {
    name: "AppContainer",
    data: function(){
        return {
            logHeadings: ["date", "count", "go?", "do?"],
            mockData,
            displayDropdown: false,
        }
    },
    components: {
        topNav
    },
    methods: {
        addForm(value){
            this.displayDropdown = value;
        }
    }
}
</script>

<style>
    .container {
        height: 926px;
        width: 428px;
        border: 10px solid midnightblue;
        font-family: Arial, Helvetica, sans-serif;
        font-size: 20px;
    }

    .table {
        width: 100%;
    }

    .headings-row {
        display: flex;
        justify-content: space-evenly;
        width: 100%;
        border: 1px solid red;
    }

    .heading {
        border: 1px solid orange;
    }

    .row {
        border: 2px solid black;
        display: flex;
        justify-content: space-evenly;
        width: 100%;
    }

    .cell {
        border: 1px solid black;
    }

    .yes {
        color: green;
    }

    .no {
        color: orangered;
    }
</style>