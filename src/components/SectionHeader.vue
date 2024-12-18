<template>
    <header class="section__header">
                <h2 class="section__title puddle-bg"> {{ title }}</h2>
                <div class="section_description">
                    <p> {{ content }}</p>
                </div>
    </header>
</template>
<script>
export default {
  props: {
    title: {
      type: String,
      required: true
    },
    content: {
      type: String,
      required: true
    }
  }
}
</script>

<style scoped lang="scss">
</style>
