<template>

  <div>
    <Return></Return>
    <div class="container">
      <ul class="responsive-table">
        <li class="table-header line">
          <div class="col col-1">Id</div>
          <div class="col col-2">Username</div>
          <div class="col col-3">Email</div>
          <div class="col col-4">Company</div>
        </li>
        <NuxtLink 
            v-for="(user, index) in users" :key="index" 
            :to="{name: 'UserDetails', params: {user: user}}"
            class="table-row line">
          <div class="col col-1" data-label="Id">{{user.id}}</div>
          <div class="col col-2" data-label="Username">{{user.username}}</div>
          <div class="col col-3" data-label="Email">{{user.email}}</div>
          <div class="col col-4" data-label="Company">{{user.company_name}}</div>
        </NuxtLink>
      </ul>        
    </div>

  </div>
</template>

<script>
export default {
  name: 'Dashboard',
  transition: '',
  data: () => {
    return {
      users: []
    }
  },

  mounted() {
    this.fetch_users()
  },

  methods: {
    fetch_users() {
      fetch('https://my-json-server.typicode.com/Neltarim/Nuxt-tests/users')
      .then((response) => response.json())
      .then((json) => this.users = json);
    },

    open_user(i) {

    }
  }
}
</script>

<style lang="scss">
  html {
    background-color: #1c242c;
    font-family: helvetica, arial, sans-serif;
  }
  .container {
    max-width: 1000px;
    margin-top: 6rem;
    margin-left: auto;
    margin-right: auto;
    padding-left: 10px;
    padding-right: 10px;
  }

  .responsive-table {
    padding: 0rem;
    
    .line {
      border-radius: 3px;
      padding: 25px 30px;
      display: flex;
      justify-content: space-between;
      margin-top: 10px;
      text-decoration: none;
      color: black;
    }
    @media only screen and (max-width:415px) {
      .line {
        padding: 20px 10px;        
      }
    }

    .table-header {
      background-color: #568588;
      color: white;
      font-size: 14px;
      text-transform: uppercase;
      letter-spacing: 0.03em;
    }
    .table-row {
      background-color: #ffffff;
      box-shadow: 0px 0px 9px 0px rgba(0,0,0,0.1);
      transition: 0.1s;
    }

    .table-row:hover {
      background-color: $green;
      box-shadow: 0px 0px 9px 0px rgba(0, 0, 0, 0.5);
      color: white;
      cursor: pointer;
    }

    .col-1 {
      flex-basis: 10%;
      @include bold-text;
    }
    .col-2 {
      flex-basis: 10%;
      text-align: left;
    }
    .col-3 {
      flex-basis: 60%;
      text-align: center;
    }
    .col-4 {
      flex-basis: 25%;
      text-align: right;
    }
    
  }
</style>