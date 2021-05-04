<template>
  <main>
    <section v-if="team" class="w-full max-w-5xl mx-auto">
      <h1 class="title">Team</h1>
      <posts post-type="team" :amount="10" />
    </section>
  </main>
</template>

<script>
export default {
  data() {
    return {
      ob: null,
    }
  },

  async asyncData({ $content, error }) {
    let team
    try {
      team = await $content('team').fetch()
    } catch (e) {
      error({ message: 'Team post not found' })
    }
    return { team }
  },
  methods: {
    async getUser() {
      this.ob = await this.$axios.$get('https://jsonplaceholder.typicode.com/todos/1')
      console.log(this.ob)
    },
  },
  created() {
    this.getUser()
  },
}
</script>
