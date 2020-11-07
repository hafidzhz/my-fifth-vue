<template>
  <teleport to="body">
    <base-dialog v-if="isInvalid" title="Invalid Input" @close="invalidate" >
      <template #default>
        <p>One of input is invalid</p>
      </template>
    </base-dialog>
  </teleport>
  <base-card>
    <form @submit.prevent="onSubmit">
      <div class="form-control">
        <label>Title</label>
        <input type="text" name="title" id="title" ref="titleInput">
      </div>
      <div class="form-control">
        <label>Description</label>
        <textarea name="description" id="description" rows="3" ref="descInput"></textarea>
      </div>
      <div class="form-control">
        <label>Link</label>
        <input type="link" name="link" id="link" ref="linkInput">
      </div>
      <div>
        <base-button type="submit">
          Add Resource
        </base-button>
      </div>
    </form>
  </base-card>
</template>

<script>
export default {
  inject: ['addResource'],
  data () {
    return {
      isInvalid: false
    }
  },
  methods: {
    onSubmit () {
      const title = this.$refs.titleInput.value
      const description = this.$refs.descInput.value
      const link = this.$refs.linkInput.value
      this.isInvalid = title.trim() === '' || description.trim() === '' || link.trim() === ''

      if (this.isInvalid) {
        return ''
      } else {
        this.addResource(title, description, link)
      }
    },
    invalidate () {
      this.isInvalid = false
    }
  }
}
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>
