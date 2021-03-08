<template>
<base-dialog v-if="isInvalid" title="Invalid Input">
    <template #default>
        <p>Please fill in all the required inputs to add a resource to the list.</p>
    </template>
    <template #actions>
        <base-button @click="closeDialog">Okay</base-button>
    </template>
</base-dialog>
<h1>Add a ressource</h1>
  <base-card>
    <form @submit.prevent="submitData">
        
        <div class="form-control">
            <base-card>
            <label for="name">Name</label>
            <input type="text" name="name" id="name" ref="titleInput">
            </base-card>
            
            <base-card>
            <label for="description">Description</label>
            <textarea name="description" id="description" ref="descriptionInput"></textarea>
            </base-card>
            
            <base-card>
            <label for="link">Link</label>
            <input type="url" name="link" id="link" ref="urlInput">
            </base-card>

            <div class="btn">
                <base-button type="submit">Add the resource</base-button>
            </div>

        </div>
    </form>
    </base-card>
</template>

<script>
import BaseButton from '../UI/BaseButton.vue';
import BaseCard from '../UI/BaseCard.vue'
import BaseDialog from '../UI/BaseDialog.vue';
export default {
  inject: ['submitResource'],
  components: { BaseCard, BaseDialog, BaseButton },
  data () {
    return {
        isInvalid: false,
    }
  },
  methods: {
      submitData() {
          const enteredTitle = this.$refs.titleInput.value;
          const enteredDescription = this.$refs.descriptionInput.value;
          const enteredUrl = this.$refs.urlInput.value;

          if (enteredTitle.trim() === '' || enteredTitle.trim() === '' || enteredUrl.trim() === '' ) {
              this.isInvalid = true;
          }
          else {
          this.submitResource(enteredTitle,enteredDescription,enteredUrl);
          }
      },
      closeDialog() {
          this.isInvalid = false;
      },
  },

}
</script>

<style scoped>

h1 {
    margin-left: 25rem;
}

.form-control {
    display: flex;
    flex-direction: column;
}

.form-control div {
    display: flex;
    flex-direction: column;
    margin: 1.5rem 0;
}

.form-control textarea{
    height: 15vh;
}


.btn {
    display: flex;
    align-items: center;
}

.form-control button {
    width: 25%;
}

</style>