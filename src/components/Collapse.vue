<style>
.collapse {
  margin-bottom: 2px;
}
.collapse .collapse-header {
  padding: 20px 20px 20px 40px;
  background: #ffffff;
  border-radius: 3px;
  position: relative;
}
.collapse .collapse-header > div {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.collapse .collapse-header h3 {
  font-size: 0.938em;
  font-weight: bold;
}
.collapse .collapse-header::before {
  -moz-transition: all .2s;
  -o-transition: all .2s;
  -webkit-transition: all .2s;
  transition: all .2s;
  content: url('../assets/arrow-down.svg');
  position: absolute;
  font-size: 0.4em;
  top: calc(50% - 0.4em);
  color: #ffffff;
  -moz-transform: rotate(0deg);
  -o-transform: rotate(0deg);
  -ms-transform: rotate(0deg);
  -webkit-transform: rotate(0deg);
  transform: rotate(0deg);
}
.collapse.is-active .collapse-header::before {
  -moz-transform: rotate(180deg);
  -o-transform: rotate(180deg);
  -ms-transform: rotate(180deg);
  -webkit-transform: rotate(180deg);
  transform: rotate(180deg);
}
.collapse .collapse-content-box {
  -moz-transition: all 2s;
  -o-transition: all 2s;
  -webkit-transition: all 2s;
  transition: all 8s;
  padding: 30px 40px;
  border-left: 2px solid #ffffff;
  border-bottom: 2px solid #ffffff;
  border-right: 2px solid #ffffff;
  border-bottom-left-radius: 3px;
  border-bottom-right-radius: 3px;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

</style>

<template>
  <div class="collapse collapse-item" :class="{ 'is-active': active }">
    <transition name="fade">
      <div class="collapse-content" v-if="active">
        <div class="collapse-content-box">
          <slot name="collapse-body"></slot>
        </div>
      </div>
    </transition>
      <div class="collapse-header touchable" role="tab" :aria-expanded="active ? 'true' : 'false'" @click.prevent="toggle">
        <slot name="collapse-header"></slot>
      </div>
  </div>
</template>

<script>

export default {
  name: "Collapse",

  data(){
    return {
      active: false
    }
  },

  props: {
    selected: {
      type: Boolean,
      required: true,
      default: false
    }
  },

  created () {
    this._isCollapseItem = true
    this.active = this.selected
  },
  ready () {
    if (this.active) {
      this.$emit('collapse-open', this.index)
    }
  },
  methods: {
    toggle () {
      this.active = !this.active
      if (this.active) {
        this.$emit('collapse-open', this.index)
      }
    }
  }
}
</script>