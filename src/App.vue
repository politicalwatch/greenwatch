<template>
  <div id="app">
    <header>
      <h1>GreenWatch</h1>
      <p class="headline">
      </p>
    </header>
    <filters
      @filter-topic="filterTopic"
      @filter-party="filterParty"
      @filter-place="filterPlace"
      />
    <div class="downloads" v-if="filteredEntries.length > 0">
      <vue-csv-downloader
        :data="filteredEntries"
        :fields="csvFields"
        :downloadName="getNameFromCSV()">
        Descargar declaraciones
      </vue-csv-downloader>
    </div>
    <listing
      :entries="filteredEntries"
      :loadedData="loadedData"
    />
    <footer>
      <a href="http://politicalwatch.es" target="_blank"><img class="watch" src="./assets/politicalwatch.png"></a> <a href="http://greenpeace.es" target="_blank"><img class="green" src="./assets/greenpeace.svg"/></a>
    </footer>
  </div>
</template>

<script>
import axios from 'axios';
import VueCsvDownloader from 'vue-csv-downloader';
import listing from './components/listing.vue';
import filters from './components/filters.vue';

export default {
  name: 'app',
  components: {
    listing,
    filters,
    VueCsvDownloader
  },

  data() {
    return {
      entries: [],
      fields: [
        "topic",
        "proposal",
        "party",
        "candidate",
        "statement",
        "source",
        "date",
        "place"
      ],
      selected_topic: '',
      selected_party: '',
      selected_place: '',
      params: [],
      loadedData: 0,
    };
  },

  computed: {
    filteredEntries() {
      return this.entries.filter(entry => entry.topic.includes(this.selected_topic) && entry.party.includes(this.selected_party) && entry.place.includes(this.selected_place));
    },
  },

  methods: {
    filterTopic(value) {
      this.selected_topic = value;
    },
    filterParty(value) {
      this.selected_party = value;
    },
    filterPlace(value) {
      this.selected_place = value;
    },
    getNameFromCSV: function() {
      const d = new Date();
      return 'greenwatch-data-' + d.toISOString() + '.csv';
    },
  },

  mounted() {
    axios
      .get('//data.greenwatch.politicalwatch.es')
      .then((response) => {
        this.entries = response.data;
        this.loadedData = response.status;
      });
  },
};
</script>

<style lang="scss">
  $primary: #2ab20b;
  $white: #f8f8f8;

  header {
    text-align: center;
  }

  footer {
    height: 50px;
    padding: 10px;
    img {
      height: 30px;
      &.green {
        float: left;
      }
      &.watch {
        float: right;
      }
    }
  }

  .downloads {
    text-align: center;
    font-size: 0.85rem;
    margin-bottom: 1rem;

    a {
      text-decoration: underline;

      &:hover {
        text-decoration: none;
      }
    }
  }
</style>
