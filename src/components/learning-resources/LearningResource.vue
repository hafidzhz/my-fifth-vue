<template>
  <li>
    <base-card>
      <div>
        <header>
          <h3>{{ title }}</h3>
          <base-button  @click="deleteResource(id)" mode="flat">Delete</base-button>
        </header>
      </div>
      <p>{{ description }}</p>
      <nav>
        <a :href="link">View Resources</a>
      </nav>
    </base-card>
  </li>
</template>

<script>
export default {
  props: ['id', 'title', 'description', 'link'],
  inject: ['deleteResource']
}
</script>

<style scoped>
li {
  margin: auto;
  max-width: 40rem;
  marker: none;
  list-style-type: none;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

h3 {
  font-size: 1.25rem;
  margin: 0.5rem 0;
}

p {
  margin: 0.5rem, 0;
}

a {
  text-decoration: none;
  color: #ce5c00;
}

a:active,
a:hover {
  color: #c89300
}
</style>
