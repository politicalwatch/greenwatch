<template>
  <div class="filters">
    <div class="styled-select">
      <select
          name="topics"
        @change="$emit('filter-topic', $event.target.value)"
      >
        <option value="">Todas las temáticas</option>
        <option value="Democracia y Contrapoder">Democracia y Contrapoder</option>
        <option value="Cambio Climático">Cambio Climático</option>
        <option value="Biodiversidad y Ecosistemas">Biodiversidad y Ecosistemas</option>
        <option value="Consumo y Ciudades">Consumo y Ciudades</option>
      </select>
    </div>

    <div class="styled-select">
      <select
        name="candidates"
        @change="$emit('filter-party', $event.target.value)"
      >
        <option value="">Todos los candidatos</option>
        <option value="Partido Popular">Casado, Pablo</option>
        <option value="Partido Socialista">Sánchez, Pedro</option>
        <option value="Unidas Podemos">Iglesias, Pablo</option>
        <option value="Ciudadanos">Rivera, Albert</option>
        <option value="Vox">Abascal, Santiago</option>
      </select>
    </div>

  </div>
</template>

<script>
export default {
  name: 'filters',
  props: [
    'topics',
    'parties'
  ],
};
</script>

<style lang="scss">
  $primary: #2ab20b;

  .filters {
    margin: 0 1rem 1rem 1rem;

    @media (min-width: 599px) {
      display: flex;
    }
  }

  .styled-select {
    border: 1px solid $primary;
    margin-bottom: 0.5rem;
    position: relative;
    width: 100%;
    overflow: hidden;

    @media (min-width: 599px) {
      margin: 0 0.5rem;
    }


    &:first-child {
      @media (min-width: 599px) {
        margin-left: 0;
      }
    }

    &:last-child {
      @media (min-width: 599px) {
        margin-right: 0;
      }
    }

    select {
      -webkit-appearance: none;
      border: 0;
      background: transparent;
      width: 105%;
      padding: 0.5rem;
      outline: none;
      font-size: 0.8rem;
    }

    &::after {
      content: "";
      display: block;
      width: 0.7rem;
      height: 0.7rem;
      border-right: 2px solid $primary;
      border-top: 2px solid $primary;
      position: absolute;
      right: 2rem;
      top: 50%;
      transform: rotate(135deg) translateX(-100%);
      pointer-events: none;
    }

  }
</style>
