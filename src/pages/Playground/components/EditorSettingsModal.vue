<template>
  <div class="modal">
    <div class="modal-background"></div>
    <div class="modal-card">
      <header class="modal-card-head">
        <p class="modal-card-title">Editor Settings</p>
        <button
          class="delete"
          aria-label="close"
          @click="$emit('close-modal')"
        ></button>
      </header>
      <section class="modal-card-body">
        <!-- Content ... -->
      </section>
      <footer class="modal-card-foot">
        <button class="button is-primary">Save changes</button>
        <button class="button is-danger">Cancel</button>
      </footer>
    </div>
  </div>
</template>