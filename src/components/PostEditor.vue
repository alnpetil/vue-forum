<template>
  <form @submit.prevent="save">
    <div class="form-group">
      <textarea
        name=""
        id=""
        class="form-input"
        cols="30"
        rows="10"
        v-model="text"
        ></textarea>
    </div>
    <div class="form-actions">
      <button class="btn-blue">Submit post</button>
    </div>
  </form>
</template>

<script>
  export default {
    props: {
      threadId: {
        required: true,
        type: String
      }
    },

    data () {
      return {
        text: ''
      }
    },

    methods: {
      save () {
        const postId = 'greatPost' + Math.random()
        const post = {
          text: this.text,
          publishedAt: Math.floor(Date.now() / 1000),
          threadId: this.threadId,
          userId: 'ALXhxjwgY9PinwNGHpfai6OWyDu2',
          '.key': postId
        }

        this.text = ''
        this.$emit('save', { post })
      }
    }
  }
</script>