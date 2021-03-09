<template>
    <div class="main-block">
        <h1> {{title}} </h1>
        <slot></slot>
    </div>
</template>

<script>
  export default {
    props: ['data', 'title'],
    data() {
      return {}
    },
    methods: {
      logWatch() {
        const result = this.data.map(i => {
          return {
            id: i.id,
            firstName: i.firstName,
            url: i.url
          }
        })
        console.log(result)
      }
    },
    components: {}
  }
</script>

<style scoped>
    .main-block {
        width: 49%;
        height: 97vh;
        border: 1px solid black;
        position: relative;
        border-radius: 30px;
        text-align: center;
        background: #eefaff;
    }

    .btn {
        position: absolute;
        bottom: 30px;
        left: 420px;

    }

</style>
