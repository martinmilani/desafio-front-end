<template>
  <div class="reloj">
    <b-card
      bg-variant="secondary"
      text-variant="white"
      :header="nombre"
      style="width: 20rem"
      class="mb-2"
      :title="valor"
    >
      <p>{{ unidad }}</p>
    </b-card>
  </div>
</template>

<script>
export default {
  props: ["nombre", "valor", "unidad"],
};
</script>
