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
        <option value="">Todos los partidos</option>
        <option value="Partido Popular">Partido Popular</option>
        <option value="Partido Socialista">Partido Socialista</option>
        <option value="Unidas Podemos">Unidas Podemos</option>
        <option value="Ciudadanos">Ciudadanos</option>
        <option value="Vox">Vox</option>
        <option value="ERC">ERC</option>
        <option value="JxCat">JxCat</option>
        <option value="Compromís">Compromís</option>
        <option value="Coalición Canaria">Coalición Canaria</option>
        <option value="PRC">PRC</option>
        <option value="BNG">BNG</option>
        <option value="Geroa Bai">Geroa Bai</option>
      </select>
    </div>

    <div class="styled-select">
      <select
          name="place"
        @change="$emit('filter-place', $event.target.value)"
      >
        <option value="">Todas los territorios</option>
        <option value="Álava">Álava</option>
        <option value="Almería">Almería</option>
        <option value="Ávila">Ávila</option>
        <option value="Baleares">Baleares</option>
        <option value="Barcelona">Barcelona</option>
        <option value="Cádiz">Cádiz</option>
        <option value="Canarias">Canarias</option>
        <option value="Cantabria">Cantabria</option>
        <option value="Castellón">Castellón</option>
        <option value="Cataluña">Cataluña</option>
        <option value="Ciudad ">Ciudad Real</option>
        <option value="Comunidad ">Comunidad Valenciana</option>
        <option value="Córdoba">Córdoba</option>
        <option value="Cuenca">Cuenca</option>
        <option value="Galicia">Galicia</option>
        <option value="Guadalajara">Guadalajara</option>
        <option value="Guipúzcua">Guipúzcua</option>
        <option value="Huesca">Huesca</option>
        <option value="Lleida">Lleida</option>
        <option value="Madrid">Madrid</option>
        <option value="Murcia">Murcia</option>
        <option value="Navarra">Navarra</option>
        <option value="Presidente ">Presidente del Partido</option>
        <option value="País ">País Vasco</option>
        <option value="Pontevedra">Pontevedra</option>
        <option value="Sevilla">Sevilla</option>
        <option value="Teruel">Teruel</option>
        <option value="Toledo">Toledo</option>
        <option value="Valencia">Valencia</option>
        <option value="Valladolid">Valladolid</option>
        <option value="Zaragoza">Zaragoza</option>
      </select>
    </div>

  </div>
</template>

<script>
export default {
  name: 'filters',
  props: [
    'topics',
    'parties',
    'places',
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
