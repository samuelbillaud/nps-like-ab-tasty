<template>
  <div class="modal-overlay" v-show="isActive">
        <div class="modal-content">
            <span class="close-button">&times;</span>
            <h1>{{ question }}</h1>
            <form>
                <ul>
                    <li v-for="(item, index) in maxNote" :key="index">
                        <input
                          type="radio"
                          name="note"
                          :value="index"
                          :id="index">
                        <label :for="index">{{ index }}</label>
                    </li>
                </ul>
                <button :disabled="isDisabled">{{ valid }}</button>
            </form>
        </div>
  </div>
</template>

<script>
export default {
  name: 'Modal',
  data () {
    return {
      question: 'Aimez-vous notre site ?',
      maxNote: 6,
      valid: 'Valider',
      isDisabled: true
    }
  },
  props: {
    isActive: {
      type: Boolean,
      required: true
    }
  },
  methods: {
    submit () {

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
