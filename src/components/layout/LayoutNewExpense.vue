<template>
  <div class="w-100 d-flex align-items-center justify-content-center">
    <button
      class="btn btn-lg btn-outline-primary w-75"
      @click="showModal = true"
      >
      Navo Gasto
    </button>

    <div class="modal fade" :class="{show: showModal}" style="padding-right: 15px; display: block;" :style="{ display: showModal ? 'block' : 'none' }">
      <div class="modal-dialog" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLiveLabel">Modal title</h5>
            <button type="button" class="close" data-dismiss="modal" aria-label="Close" @click="closeModal()">
              <span aria-hidden="true">×</span>
            </button>
          </div>
          <div class="modal-body">
            <p>Woohoo, you're reading this text in a modal!</p>
          </div>
          <div class="modal-footer">
            <button
              type="button"
              class="btn btn-secondary"
              @click="closeModal()"
              >
              Close
            </button>
            <button
              type="button"
              class="btn btn-primary"
              >
              Save changes
            </button>
          </div>
        </div>
      </div>
    </div>

    <div class="modal-backdrop fade" :style="{ display: showModal ? 'block' : 'none' }" :class="{show: showModal}"></div>
  </div>
</template>

<script>
export default {
 data: () => ({ showModal: false }),
 methods: {
   closeModal () {
     this.showModal = false
   }
 }
}
</script>

<style lang="scss" scoped>

</style>
