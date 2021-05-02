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
  async asyncData({ $content, error }) {
    let posts
    try {
      posts = await $content('team').fetch()
    } catch (e) {
      error({ message: 'Team posts not found' })
    }
    return { posts }
  },
}
</script>
