<script>
  import { butter } from '@/buttercms'
  export default {
    name: 'customer-page',
    data() {
      return {
        page: {
          fields: {}
        }
      }
    },
    methods: {
      getPage() {
        butter.page.retrieve('*', 'hello')
          .then((res) => {
            console.log(res.data.data)
            this.page = res.data.data
          }).catch((res) => {
            console.log(res)
          })
      }
    },
    created() {
      this.getPage()
    }
  }
</script>

<template>
  <div id="customer-page">
    <h1>{{ page.fields.first_name }}</h1>
   <router-link :to="'/customers/'"><button> {{ page.fields.whats_the_day }}</button></router-link>
  </div>
</template>