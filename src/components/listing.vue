<template>
  <div class="listing-wrapper">
    <h4 class="loading" v-if="!entries.length && !loadedData">Cargando datos</h4>
    <h4 class="loading" v-if="!entries.length && loadedData">Aún no hay declaraciones registradas durante la campaña.</h4>
    <ul class="listing">
      <li class="listing__item" v-for="(entry, i) in entries" :key="i">
        <p class="listing__author">
        <strong>{{ entry.candidate }}</strong> ({{ entry.party }}) <time>el {{ entry.date }}</time>
        </p>
        <p class="listing__topic">
          <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="#2ab20b" stroke-width="1" stroke-linecap="round" stroke-linejoin="round"><line x1="8" y1="6" x2="21" y2="6"></line><line x1="8" y1="12" x2="21" y2="12"></line><line x1="8" y1="18" x2="21" y2="18"></line><line x1="3" y1="6" x2="3" y2="6"></line><line x1="3" y1="12" x2="3" y2="12"></line><line x1="3" y1="18" x2="3" y2="18"></line></svg>
          {{ entry.topic }}
          <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="#2ab20b" stroke-width="1" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h13M12 5l7 7-7 7"/></svg>
          {{ entry.proposal }}
        </p>
        <blockquote class="listing__quote">
          {{ entry.statement }}
        </blockquote>
        <div class="listing__meta">
          <div class="listing__place">
            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="#2ab20b" stroke-width="1" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="10" r="3"/><path d="M12 21.7C17.3 17 20 13 20 10a8 8 0 1 0-16 0c0 3 2.7 6.9 8 11.7z"/></svg> <span class="place">{{ entry.place }}</span>
          </div>
          <div class="listing__source">
            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="#2ab20b" stroke-width="1" stroke-linecap="round" stroke-linejoin="round"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg>
            <a target="_blank" :href="entry.source">Fuente</a>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'listing',
  props: {
    entries: Array,
    loadedData: Number,
  },
};
</script>

<style lang="scss">
  $primary: #2ab20b;

  .loading {
    text-align: center;
    font-style: italic;
    color: $primary;
  }

  .listing {
    list-style: none;
    padding: 0;
    margin: 0;
    margin: 0 1rem 1rem 1rem;

    &__item {
      box-shadow: 0 0 1rem rgba(0,0,0,0.1);
      padding: 1rem;
      margin-bottom: 1rem;
      border: 1px solid rgba($primary, 0.2);
    }

    &__author {
      margin: 0 0 1rem 0;

      strong {
        margin-right: 0.5rem;
      }

      time {
        font-style: italic;
        font-size: 0.75rem;
      }

    }

    &__topic {
      font-size: 0.75rem;
    }

    &__quote {
      padding: 0;
      margin: 0 0 1rem 0;
      line-height: 1.4;
      position: relative;
      padding-left: 2rem;

      &::before {
        font-family: 'Times New Roman', Times, serif;
        content: open-quote;
        font-size: 3.5rem;
        line-height: 0.7;
        position: absolute;
        color: rgba(0,0,0, 0.2);
        left: 0;
        top: 0;
      }

      &::after {
        visibility: hidden;
        content: close-quote;
      }
    }

    &__meta {
      margin: 0 -1rem -1rem -1rem;
      background: rgba($primary, 0.05);
      padding: 1rem 1rem 0.5rem 1rem;
      font-size: 0.75rem;

      @media (min-width: 599px) {
        display: flex;
        justify-content: space-between;
      }

      svg {
        vertical-align: text-bottom;
        margin-right: 0.5rem;
      }
    }

    &__place {
      margin-bottom: 0.5rem;
    }

    &__source {
      margin-bottom: 0.5rem;
    }

  }
</style>
