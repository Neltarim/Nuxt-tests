<template>
  <div>
    <Return :to="'/Dashboard'"></Return>

    <div class="container">
      <div class="card">
        <div class="card-body">

          <div class="row">
            <h4 class="bold">id</h4>
            <h4>{{user.id}}</h4>
          </div>
          <hr>
          <div class="row">
            <h4 class="bold">username</h4>
            <h4>{{user.username}}</h4>
          </div>
          <hr>
          <div class="row">
            <h4 class="bold">email</h4>
            <h4>{{user.email}}</h4>
          </div>
          <hr>
          <div class="row">
            <h4 class="bold">company</h4>
            <h4>{{user.company_name}}</h4>
          </div>

        </div>
      </div>
      <div class="multi">
        <div class="card semi">
          <div class="card-header">
            <h1>Posts</h1>
          </div>
          <div v-for="post in user.posts" :key="post" class="post">
            <h2>{{post.title}}</h2>
            <h4>{{post.text}}</h4>
          </div>
        </div>   
        <div class="card semi">
          <div class="card-header">
            <h1>Todos</h1>
          </div>
          <div v-for="todo in user.todos" :key="todo" class="todo">
            <h2>{{todo.desc}}</h2>
            <font-awesome-icon v-if="todo.done" 
              class="finished icon" icon="check" size="2x"/>
            <font-awesome-icon v-if="!todo.done" 
              class="unfinished icon" icon="exclamation" size="2x"/> 
          </div>
        </div>   
      </div>
    </div>    
  </div>

</template>

<script>
export default {
  name: 'UserDetails',
  data:() => {
    return {
      user: {},
    }
  },

  mounted() {
    this.user = this.$route.params.user
  }
}
</script>

<style lang="scss">
.card {
    box-shadow: 0 1px 3px 0 rgba(0,0,0,.1), 0 1px 2px 0 rgba(0,0,0,.06);
}

.card {
    background-color: #fff;
    background-clip: border-box;
    border: 0 solid rgba(0,0,0,.125);
    border-radius: .25rem;
}

.card-body {
    min-height: 1px;
    padding: 1rem;
}

.card-header {
  text-align: center;
}

.row {
  display: flex;
  justify-content: space-between;
  padding-inline: 1rem;
}

.multi { display: flex; }
.multi > :first-child { margin-right: 1rem; } 

@media only screen and (max-width:415px) {
  .multi { display: block; }
  .card-header { padding-top: .2rem; }
}

.semi {
  height: 100%;
  width: 100%;
  margin-top: 1rem;
}

.post {
  margin: 1rem;
  padding-inline: 3rem;
  padding-block: 1rem;
  margin-bottom: 20px; 
  padding-bottom:20px; 
  border-bottom: 1px solid rgb(170, 170, 170);
}
.post:last-child { border-bottom: none; }

.todo {
  margin: 1rem;
  padding-inline: 3rem;
  padding-block: 1rem;
  display: flex;
  justify-content: space-between;
  vertical-align: middle;
  border-bottom: 1px solid rgb(170, 170, 170);

  .icon {
    padding-top: 1rem;
    width: 2rem;
  }

  .unfinished { color: $red; }
  .finished { color: $green; }
}

.todo:last-child { border-bottom: none; }
</style>