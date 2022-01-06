<template>
<div v-bind:class="playerClass">
  <span v-html="{{ WelcomeMessage }}" v-hide></span>
  <form v-hide>
    <input name="player" placeholder="Votre nom" v-border/>
    <button type="submit">Jouer</button>
  </form>
</div>
</template>

<script>
export default {
  name: "Player",
  created: function () {
    this.WelcomeMessage = this.player ? 'Bonjour' + this.player + '!' : ''
  },
  directives: {
    border: function(el, binding) {
      el.style.borderColor = binding.arg
    },
    hide: function(el, binding, vnode) {
      let isForm = vnode.tag === 'form'
      let player = vnode.context.player;

      if(isForm) {
        el.style.display = player ? 'none' : 'block';
      } else {
        el.style.display = player ? 'block' : 'none';
      }

    }
  }
}
</script>

<style scoped>
  .player form {
    display:none;
  }

  .playerForm span {
    display: none;
  }
</style>