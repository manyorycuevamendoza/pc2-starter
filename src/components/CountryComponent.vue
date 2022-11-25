<script>
export default {
  name: "CountryComponent",
  props: [
    "name",
    "capital",
    "currency_name",
    "currency",
    "region",
    "code",
    //: crear una propiedad para determinar si al componente se le puede hacer click
    //la propiedad debe llamarse "clickable" y debe ser booleana
    "clickable",

  ],
};
</script>

<template>
  <!--: Utilizar la propiedad creada para controlar el click. Cuando el componente es "clickeable", redirigir a la pagina del pais.
  Mira las rutas para ver como redirigir al usuario.-->
  <div
    class="country"
    :class="{ clickable: clickable }"
    @click="clickable ? $router.push(`/country/${code}`) : null"
  >
  <!--: Poblar el HTML con las propiedades. Usar https://countryflagsapi.com/png/${code}-->
    <h1>{{ name }}</h1>
    <img :src="`https://countryflagsapi.com/png/${code}/flat/64.png`" />
    <p>Capital: {{ capital }}</p>
    <p>Moneda: {{ currency_name }} ({{ currency}})</p>
    <p>Región: {{ region }}</p>

    <img
      width="400"
      height="400"
    />
  <img
      width="200"
      height="200"
    />
  </div>
</template>

<style scoped>
.country {
  padding: 2px;
  white-space: nowrap;
  width: 350px;
  height: 350px;
  border-style: solid;
  border-radius: 5px;
  border-color: grey;
}

.country-hover:hover {
  background-color: rgb(49, 49, 49);
  cursor: pointer;
}

h1 {
  overflow: hidden;
  text-overflow: ellipsis;
}
</style>
