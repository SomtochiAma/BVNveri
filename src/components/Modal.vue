<template>
    <transition name="modal">
    <div class="modal-mask">
      <div class="modal-wrapper">
        <div class="modal-container">
          <div class="close"><span @click="$emit('close')">x</span></div>
          <div class="modal-header">
            <slot name="header">
              Hey there,
            </slot>
          </div>

          <div class="modal-body">
            <slot name="body">
              default body
            </slot>
          </div>

        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
    name: "Modal",
    data() {
        return {
            showModal: false
        }
    }
}
</script>

<style scoped>

.close {
  text-align: right;
}

.close:hover {
  cursor: pointer;
}

span {
  font-size: 20px;
  color: grey;
  border: 1px solid #c4c4c4;
  padding: 2px 5px;
  border-radius: 5px;
  text-align: center;
}

.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, .5);
  display: table;
  transition: opacity .3s ease;
}

.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}

.modal-container {
  width: 50%;
  margin: 0px auto;
  padding: 20px 30px;
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, .33);
  transition: all .3s ease;
  text-align: center
}

.modal-header h3 {
  margin-top: 0;
  color: #42b983;
}

.modal-body {
  margin: 20px 0;
}

.modal-default-button {
  float: right;
}

/*
 * The following styles are auto-applied to elements with
 * transition="modal" when their visibility is toggled
 * by Vue.js.
 *
 * You can easily play with the modal transition by editing
 * these styles.
 */

.modal-enter {
  opacity: 0;
}

.modal-leave-active {
  opacity: 0;
}

.modal-enter .modal-container,
.modal-leave-active .modal-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}

@media screen and (max-width: 600px) {
    .modal-container {
      width: 70%
    }
}

</style>
