<template>
  <div class="forum-wrapper">
    <div class="col-full push-top">
      <div class="forum-header">
        <div class="forum-details">
          <h1>{{ forum.name }}</h1>
          <p class="text-lead">{{ forum.description }}</p>
        </div>
        <a href="new-thread.html" class="btn-green btn-small">Start a thread</a>
      </div>
    </div>
    <div class="col-full push-top">
      <Threadlist :threads="threads"/>
    </div>
  </div>
</template>

<script>
  import sourceData from '@/data'
  import Threadlist from '@/components/ThreadList'

  export default {
    components: {
      Threadlist
    },
    props: {
      id: {
        required: true,
        type: String
      }
    },
    computed: {
      forum () {
        return sourceData.forums[this.id]
      },

      threads () {
        return Object.values(sourceData.threads)
          .filter(thread => thread.forumId === this.id)
      }
    }
  }
</script>

<style scoped>
  .forum-wrapper {
    width: 100%;
  }
</style>
