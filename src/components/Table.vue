<template>
  <div class="p-10">
    <table>
      <thead>
        <tr>
          <th class="border-2 p-2 text-left">Name</th>
          <th class="border-2 p-2 text-left">Age</th>
          <th class="border-2 p-2 text-left">Profession</th>
          <th class="border-2 p-2 text-left">Year of birth</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td class="border-2 p-2">Manoj</td>
          <td class="border-2 p-2">24</td>
          <td class="border-2 p-2">Software Developer</td>
          <td class="border-2 p-2">1997</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'Table',
  data() {
    return {
      rows: [],
      columns:[]
    }
  }
}
</script>