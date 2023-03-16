<template>
  <div class="contenido">
    <h1 class="texto">
      SELECT evento.nombre, COALESCE(SUM(entradas.costo),0) as recaudacion
      <br />
      FROM evento <br />
      LEFT JOIN entradas ON evento.id = entradas.id_evento<br />
      GROUP BY evento.id, evento.nombre<br />
      ORDER BY recaudacion DESC;
    </h1>
  </div>
</template>

<script>
export default {};
</script>

<style>
.contenido {
  width: 100%;
  margin-top: 50px;
}
.texto {
  text-align: left;
}
</style>
