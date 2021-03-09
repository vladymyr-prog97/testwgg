<template>
    <div id="app">
        <main-block :data="friends" title="FRIEND LIST">
            <draggable
                    :list="friends"
                    group="friendsapp"
                    ghostClass="on-drag"
                    animation="200"
            >
                <friend v-for="person in friends" :id="person.id" :url="person.picture.data.url" :name="person.name"
                        :key="person.id"></friend>
                <div v-if="friends.length === 0">Список пока что пуст перетащите сюда друзей, что-бы заполнить данную
                    колонку
                </div>
                <login-face-book @auth="auth"></login-face-book>
            </draggable>
        </main-block>
        <main-block :data="secondArray" title="SELECTEND FRIENDS">
            <div>
                <draggable
                        :list="secondArray"
                        group="friendsapp"
                        ghostClass="on-drag"
                        animation="200"
                >

                    <friend v-for="person in secondArray" :id="person.id" :url="person.picture.data.url"
                            :name="person.name"
                            :key="person.id"></friend>
                    <div v-if="secondArray.length === 0">Список пока что пуст перетащите сюда друзей, что-бы заполнить
                        данную колонку
                    </div>
                    <button @click="wiewSecondArr" class="btn position">Save</button>
                </draggable>
            </div>
        </main-block>
    </div>
</template>


<script>


  import mainBlock from "./components/mainBlock";
  import friend from "./components/friend";
  import LoginFaceBook from "./components/LoginFaceBook";
  import draggable from 'vuedraggable'  // drag&drop сделал через этот плагин, постараюсь научиться реализовывать его без сторонних библиотек
                                        // так как этот плагин мне не особо нравиться и лучше реализовывать своими руками
  export default {
    name: 'App',
    data() {
      return {
        friends: [],
        secondArray: []
      }
    },
    methods: {
      auth(data) {
        console.log(data)
        console.log(this.friends)
        this.friends = data.friends // закидываем данные друзей в массив для вывода
      },
      wiewSecondArr() {
        console.log(this.secondArray) // вывод списка друзей второй колонки
      }
    },
    components: {
      mainBlock,
      friend,
      draggable,
      LoginFaceBook
    }
  }
</script>


<style>
    #app {
        display: flex;
        justify-content: space-between;
        position: relative;
    }

    .on-drag {
        background: #eefaff;
        color: #FFF;
    }

    .btn {
        position: absolute;
        color: #42b983;
        place-content: center;
        place-items: center;
        width: fit-content;
        border-radius: 99px;
        letter-spacing: 0.05em;
        border: 1px solid #42b983;
        text-decoration: none;
        text-transform: uppercase;
        margin-right: 10px;
        padding: 0.5rem 1.5rem;
        white-space: nowrap;
        font-weight: 700;
        outline: none;
        background: #fff;
        transition: all 0.22s;
        cursor: pointer;
        bottom: 50px;
        left: 300px;
    }

    .position {
        left: 430px;
    }
</style>


<!--{-->
<!--status: 'connected',-->
<!--authResponse: {-->
<!--accessToken: '...',-->
<!--expiresIn:'...',-->
<!--signedRequest:'...',-->
<!--userID:'...'-->
<!--}-->
<!--}-->



