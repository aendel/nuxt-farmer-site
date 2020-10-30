<template>
  <div>
    {{
      history
    }}
  </div>
</template>

<script>
import historyQuery from '~/apollo/queries/histories/history.gql'

export default {
  data() {
    return {
      history: Object
    }
  },
  apollo: {
    history: {
      prefetch: true,
      query: historyQuery,
      variables () {
        return { id: this.$route.params.id }
      }
    }
  }
}
</script>

<style>
</style>