<template>
    <div>
        <button @click="logIn" class="btn" v-if="isOpen">Авторизоваться через FB</button>
    </div>
</template>

<script>

  export default {
    data() {
      return {
        person: {
          userID: '',
          name: '',
          accessToken: '',
          email: '',
          friends: null
        },
        isOpen: true
      }
    },
    methods: {
      //логинизация в FB остальная логика в index.html
      //обойти запрет FB для получения друзей я не смог, смог только реализовать те которые уже использовали это приложение, выводит только их
      // это запрет самого FB, возможно можно как-то это обойти но к сожалению я не смог найти
      logIn() {
        window.FB.login((response) => {
          if (response.status === 'connected') {
            this.person.userID = response.authResponse.userID
            this.person.accessToken = response.authResponse.accessToken
            window.FB.api('/me?fields=id,name,first_name,last_name,email,friends{picture,name,first_name,last_name}', (userData) => {
              this.person.name = userData.name
              this.person.email = userData.email
              this.person.friends = userData.friends.data
              this.$emit('auth', this.person)
              this.isOpen = false
            })

          }
        }, {scope: 'public_profile,email,user_friends'})

      }
    }
  }

</script>

<style>
    .button {
        color: white;
        min-width: 150px;
        background-color: #000000a1;
        height: 2.5rem;
        border-radius: 2rem;
        font-weight: 400;
        font-size: 0.8rem;
    }
</style>
