<template>
  <div>
    <nuxt-content :document="page" />
  </div>
</template>
<script>
export default {
  name: 'About',
  async asyncData({ $content, params, error }) {
    const page = await $content('about')
      .fetch()
      .catch(err => {
        error({ statusCode: 404, message: 'Page not found', err })
      })

    return {
      page
    }
  }
}
</script>
