<template>
  <nav aria-label="Page navigation example">
    <ul class="pagination">
      <li class="page-item">
        <router-link class="page-link" :to="{ name: 'Sala', query: { page: page - 1 } }">Anterior</router-link>
      </li>
      <li class="page-item">
        <router-link class="page-link" to="">1</router-link>
      </li>
      <li class="page-item">
        <a class="page-link" :to="{ name: 'Sala', query: { page: page + 1 } }">Siguente</a>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
    props: {
    siguente: String,
    page: Number
  }
}
</script>

