<template>
  <div v-if="obra" class="card" style="width: 50%">
    <img :src="obra.photo" class="card-img-top" alt="" />
    <div class="card-body">
      <h5 class="card-title">{{ obra.author }}</h5>
      <p class="card-text">
        {{ obra.title }}
      </p>
    <router-link :to="{ name: 'DetalleObra', params: { id: obra.id }}"
   class="btn btn-primary">Leer mas
    </router-link>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    obra: Object,
  },
};
</script>
