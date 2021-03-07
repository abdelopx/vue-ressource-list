<template>
  <li>
      <base-card>
          <header>
              <h3>{{title}}</h3>
              <base-button>Delete</base-button>
          </header>
      
      <p>{{description}}</p>
      <nav>
          <a :href="link">View Resource</a>
      </nav>
      </base-card>
  </li>
</template>

<script>


export default {
    props: ['title','description','link']

}
</script>

<style scoped>
li {
    margin: auto;
    max-width: 40rem;
}

header {
    display: flex;
    justify-content: space-between;
    align-items: center;
}
h3 {
    font-size: 1.5rem;
    margin: 1.2rem 0;
}
p {
    margin: 0.5rem 0;
}

a {
    text-decoration: none;
    color: rgb(255, 188, 62);
}

a:hover,
a:active {
    color:orangered;
}


</style>