<template>
  <div>
    <div
      class="d-flex wrapper fill-height justify-center mx-auto align-center px-2"
    >
      <v-card class="my-5" min-width="80%" dark>
        <v-card-title>
          Countries Stats on Corona Virus
          <v-spacer></v-spacer>
          <div>
            <v-text-field
              v-model="search"
              append-icon="mdi-magnify"
              placeholder="search for country..."
              rounded
              hide-details
              dense
              dark
            ></v-text-field>
          </div>
        </v-card-title>
        <v-data-table
          :headers="headers"
          :items="desserts"
          :search="search"
          :sort-by="['TotalConfirmed']"
          :sort-desc="[true]"
          :items-per-page="perpage"
        >
        </v-data-table>
      </v-card>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      search: '',
      value: [423, 446, 675, 510, 590, 610, 760],
      headers: [
        {
          text: 'Country',
          align: 'start',
          sortable: true,
          value: 'Country'
        },
        { text: 'Total Confirmed', value: 'TotalConfirmed' },
        { text: 'Total Deaths', value: 'TotalDeaths' },
        { text: 'Total Recovered', value: 'TotalRecovered' }
      ],
      desserts: [],
      perpage: 5
    }
  },
  async created() {
    let summaryData = await axios.get('https://api.covid19api.com/summary')
    this.desserts = summaryData.data.Countries
  }
}
</script>
<style scoped>
.wrapper {
  min-height: 85vh;
  max-width: 1200px;
}
</style>
