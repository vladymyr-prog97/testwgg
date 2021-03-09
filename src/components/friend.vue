<template>
    <div class="friend">
        <div class="ava">
            <img :src="url" alt="">
        </div>
        <div class="text">
            {{name}}
        </div>
    </div>
</template>

<script>
  export default {
    props: ['id', 'url', 'name'],
    data() {
      return {}
    }
  }
</script>

<style scoped>
    .friend {
        display: flex;
        border: 1px solid black;
        margin: 10px;
        border-radius: 20px;
        width: 70%;
        background: white;
    }

    .ava img {
        width: 50px;
        height: 50px;
        margin: 12px;
        border-radius: 50%;
    }

    .text {
        margin-top: 25px;
        margin-left: 10px;
        font-family: "Roboto Light";
        font-size: 20px;
    }
</style>
