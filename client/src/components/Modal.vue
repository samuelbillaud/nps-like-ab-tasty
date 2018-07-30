<template>
  <div class="modal-overlay" v-show="isActive">
    <div class="modal-content">
      <span class="close-button" @click="closeModal">&times;</span>
      <h1>{{ question }}</h1>
      <form @submit.prevent="onSubmit">
          <ul>
              <li v-for="(item, index) in notes" :key="index">
                <input-radio
                  name="note"
                  :id="item"
                  :value="item"
                  :valueRadio="item"
                  @input="chooseNote"
                ></input-radio>
              </li>
          </ul>

          <input-text
            name="comment"
            placeholder="Votre message ici"
            @input="writeComment"
          ></input-text>

          <button :disabled="!userNote || !comment">{{ valid }}</button>
      </form>
    </div>
  </div>
</template>

<script>
import InputRadio from '@/components/InputRadio'
import InputText from '@/components/InputText'

export default {
  name: 'Modal',
  data () {
    return {
      question: 'Aimez-vous notre site ?',
      notes: ['0', '1', '2', '3', '4', '5'],
      valid: 'Valider',
      isDisabled: true,
      userNote: null,
      comment: null
    }
  },
  components: {
    InputRadio,
    InputText
  },
  props: {
    isActive: {
      type: Boolean,
      required: true
    }
  },
  methods: {
    chooseNote (value) {
      this.userNote = value
    },
    writeComment (value) {
      this.comment = value
    },
    closeModal () {
      this.$emit('closeModal')
    },
    onSubmit () {
      console.log('onSubmit')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.modal-overlay {
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  transform: scale(1.1);
  transition: visibility 0s linear 0.25s, opacity 0.25s 0s, transform 0.25s;
}

.modal-content {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: white;
  padding: 1rem 1.5rem;
  width: 24rem;
  border-radius: 0.5rem;
}

.close-button {
  float: right;
  width: 1.5rem;
  line-height: 1.5rem;
  text-align: center;
  cursor: pointer;
  border-radius: 0.25rem;
  background-color: lightgray;
}

.close-button:hover {
  background-color: darkgray
}
</style>
