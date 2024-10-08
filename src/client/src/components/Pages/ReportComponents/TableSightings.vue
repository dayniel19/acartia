<template>

  <!-- Third column-->
  <div class="bottom-row table-row-container">
    <div class="table-header-container">

      <div class="table-header">
        <h3>Table Sighting</h3>
      </div>

      <div class="table-input-container">
        <div class="date-content ">
          <span id="date-label">Date</span>
          <input class="date-input" type="date" id="dateBegin" name="dateBegin" v-model="dateBegin">
        </div>

        <div class="species-content ">
          <span id="date-label">Species</span>
          <select class="species-select" name="species" id="species" v-model="species">
            <option value="allSpecies">All Species</option>
            <option v-for="option in speciesOptions" :key="option" :value="option">{{ option }}</option>
          </select>
        </div>

        <div class="contributor-content ">
          <span id="date-label">Contributor</span>
          <select class="contributor-select" name="contributor" id="contributor" v-model="contributor">
            <option value="allContributors">All Contributors</option>
            <option v-for="option in contributorOptions" :key="option" :value="option">{{ option }}</option>
          </select>
        </div>
      </div>
    </div>


    <table class="table table-bordered">
      <thead>
        <tr>
          <th>Sighting ID</th>
          <th>Date</th>
          <th>Contributor</th>
          <th>Species</th>
          <th>Location</th>
          <th>Reports</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(sighting, index) of tableSightings" :key="index">
          <td>{{ index + 1 }}</td>
          <td>{{ sighting.properties.created }} </td>
          <td>{{ sighting.properties.entity }}</td>
          <td>{{ sighting.properties.type }}</td>
          <td>Lat: {{ sighting.geometry.coordinates[0] }} Long: {{ sighting.geometry.coordinates[1] }} </td>
          <td><a href="#" class="text-primary">View Reports</a></td>
        </tr>
      </tbody>
    </table>

    <div v-if="!viewingMore" class="view-more">
      <a @click="toggleViewMore">View More <img src="../../../assets/Icon-arrow.svg" alt="Icon" width="40"
          height="40"></a>
    </div>

    <div v-else class="view-more">
      <a @click="toggleViewMore">View Less <img src="../../../assets/Icon-arrow.svg" alt="Icon" width="40"
          style="transform: rotate(180deg);" height=" 40"></a>
    </div>
  </div>

</template>

<script>
export default {
  name: 'TableSightings',
  data() {
    return {
      viewingMore: false
    }
  },
  methods: {
    toggleViewMore() {
      this.viewingMore = !this.viewingMore
    }
  },
  computed: {
    contributor: {
      get() {
        return this.$store.state.tableFilters.contributor
      },
      set(value) {
        this.$store.commit('setTableFilterContributor', value)
      },
    },
    species: {
      get() {
        return this.$store.state.tableFilters.species
      },
      set(value) {
        this.$store.commit('setTableFilterSpecies', value)
      },
    },
    dateBegin: {
      get() {
        return this.$store.state.tableFilters.dateBegin
      },
      set(value) {
        this.$store.commit('setTableFilterDateBegin', value)
      },
    },
    dateEnd: {
      get() {
        return this.$store.state.tableFilters.dateEnd
      },
      set(value) {
        this.$store.commit('setTableFilterDateEnd', value)
      },
    },
    tableSightings() {
      if (this.viewingMore) {
        return this.$store.getters.getSightings
      } else {
        return this.$store.getters.getSightings.slice(0, 5)
      }
    },
    //same as the map options saved in the store. Reusable filed for the table.
    contributorOptions: {
      get() {
        return this.$store.state.mapOptions.contributors
      },
    },
    speciesOptions: {
      get() {
        return this.$store.state.mapOptions.species
      },
    },
  },
}

</script>


<style scoped>
.bottom-row {
  border-radius: 1rem;
  background: white;
  padding: 1.5rem;
}

.table-row-container {
  display: flex;
  flex-direction: column;
  width: 100%;
  background: white;
}

.table-header-container {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  margin-bottom: 1rem;
}

.table-input-container {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  gap: 10px;
}

.date-input,
.species-select,
.contributor-select {
  display: flex;
  width: 100%;
  height: 3rem;
  padding: 0.8125rem 0.75rem;
  justify-content: center;
  align-items: center;
  gap: 0.625rem;
  flex-shrink: 0;
  align-self: stretch;
  border-radius: 0.375rem;
  background: var(--Neutrals-White, #FFF);
  color: var(--Neutrals-Gray-80, #3D3951);
  font-family: Montserrat;
  font-size: 1rem;
  font-style: normal;
  font-weight: 400;
  line-height: 140%;
}

.contributor-content,
.species-content,
.date-content {
  display: flex;
  width: 15rem;
  height: 4.5625rem;
  flex-direction: column;
  align-items: flex-start;
}

#date-label {
  color: var(--Neutrals-Gray-80, #3D3951);
  font-family: Mukta;
  font-size: 0.875rem;
  font-style: normal;
  font-weight: 400;
  line-height: 1.1875rem;
  letter-spacing: -0.0175rem;
  margin-bottom: 5px;
}

.table-container {
  padding: 2rem;
  background-color: #f8f9fa;
  border-radius: 15px;
}

table {
  color: var(--Neutrals-Black, #0C0826);
  text-align: center;
  font-family: Mukta;
  font-size: 1.125rem;
  font-style: normal;
  font-weight: 500;
  line-height: 1.375rem;
  letter-spacing: -0.0225rem;
}

.table th {
  background-color: #d4c8fc;
  color: #2c2c54;
  text-align: center;
  vertical-align: middle;
  padding: 1.37625rem 0rem 1.37375rem 0rem;
}

.table td {
  text-align: center;
  vertical-align: middle;
  color: #2c2c54;
  padding: 1.375rem;
}

a {
  text-decoration: none;
}

.view-more {
  text-align: right;
  padding-top: 10px;
}

.view-more a {
  color: #0C0826;
  text-decoration: none;
  font-family: Mukta;
  font-size: 1.5rem;
  font-style: normal;
  font-weight: 500;
  line-height: 105%;
}

.view-more a:hover {
  text-decoration: underline;
}
</style>
