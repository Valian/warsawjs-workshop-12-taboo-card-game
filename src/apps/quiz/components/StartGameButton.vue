<template>
    <button
      class="button"
      :disabled="tryAgainLoading"
      @click="tryAgain">
      <o-loading :loading="tryAgainLoading">
        {{ label }}
      </o-loading>
    </button>
</template>

<script>
  export default {
    props: {
      label: {
        type: String,
        default: 'Start game'
      }
    },
    loading: ['tryAgain'],
    methods: {
      tryAgain () {
        return this.$store.dispatch('quiz/initGame')
          .then(() => this.$router.push({name: 'play'}))
      }
    }
  }
</script>
