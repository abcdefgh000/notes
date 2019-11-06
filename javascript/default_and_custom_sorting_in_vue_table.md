# Default and Custom Sorting in VUE table

References
* https://v15.vuetifyjs.com/en/components/data-tables#api
* https://stackoverflow.com/questions/52678905/how-to-use-vutifys-custom-sort

Code example
```js
<template>
  <v-data-table
    :headers="queryHeaders"
    :items="allPerformanceData"
    :pagination.sync="pagination"
    :custom-sort="customSort">

...

<script>
...
      pagination: {
        rowsPerPage: 30,
        // default initial sorting
        sortBy: 'numQuestions',
        descending: true,
      },
    };
  },
  methods: {
    // curColIsDesc is a boolean, according to vutify's setting,
    // it has 3 possible values: true, false and null,
    // null means the current column is not sorted
    customSort(items, curColName, curColIsDesc) {
      console.log('curColName = ', curColName);
      console.log('curColIsDesc = ', curColIsDesc);

      items.sort((row1, row2) => {
        // for col `goldenQuestionCorrectness`, sort by col `goldenAccuracy`
        if (curColName === 'goldenQuestionCorrectness') {
          if (curColIsDesc) {
            return row2.goldenAccuracy - row1.goldenAccuracy; // descending
          }
          return row1.goldenAccuracy - row2.goldenAccuracy; // ascending
        }
        // for col `questionCorrectness`, sort by col `accuracy`
        else if (curColName === 'questionCorrectness') {
          if (curColIsDesc) {
            return row2.accuracy - row1.accuracy; // descending
          }
          return row1.accuracy - row2.accuracy; // ascending
        }
        // for other string cols, use string sort
        else if (curColName === 'userName') {
          if (curColIsDesc) {
            return row2[curColName].localeCompare(row1[curColName]); // descending
          }
          return row1[curColName].localeCompare(row2[curColName]); // ascending
        }
        // for other numerical cols, use numerical sort
        else {
          if (curColIsDesc) {
            return row2[curColName] - row1[curColName]; // descending
          }
          return row1[curColName] - row2[curColName]; // ascending
        }
      });
      return items;
    }
  }
};
</script>
```
