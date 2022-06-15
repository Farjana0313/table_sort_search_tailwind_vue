<template>
  <div class="p-10">
    <div>
      <input type="text" class="border-solid border-2 mb-5 rounded h-5 w-64 p-2" placeholder="Search Record" @input="onSearch">
    </div>
    <table>
      <thead>
        <tr>
          <th v-for="(column, index) in columns" :key="index" class="border-solid border-2 p-2 text-left" @click="sortRecords(index)">{{ column }}</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(row,index) in rows" :key="index">
          <td v-for="(rowItem, itemIndex) in row" :key="itemIndex" class="border-solid border-2 p-2">{{ rowItem }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>

const performSearch = (rows, term) => {
  const results = rows.filter(
    row=>row.join("").toLowerCase().includes(term.toLowerCase())
  )
  return results;
}

export default {
  name: 'Table',
  data() {
    return {
      rawRows: [
        [
          "Manoj", "24", "Software Developer", "1997"
        ],
        [
          "Jhoni", "26", "Lawyer", "1995"
        ],
        [
          "Sams", "27", "Lawyer", "1995"
        ],
        [
          "William", "28", "Lawyer", "1996"
        ],
        [
          "Anna", "26", "Lawyer", "1997"
        ]
      ],
      rows:[],
      columns: [
        'Name',
        'Age',
        'Profession',
        'Year of birth'
      ],
      sortIndex: null,
      sortDirection:null,
    }
  },
  methods: {
    onSearch(e) {
      const term = e.target.value;
      this.rows = performSearch(this.rawRows, term);
    },
    sortRecords(index) {
      this.sortIndex = index;
      this.rows = this.rows.sort(
        (rowA, rowB) => {
          return rowA[index].localeCompare(rowB[index])
        }
      )
    }
  },
  mounted() {
    this.rows = this.rawRows;
  }
}
</script>