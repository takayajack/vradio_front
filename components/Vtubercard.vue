<template>
<transition mode="out-in" name="bounce">
<div class="card column is-2 is-12-tablet-only" v-if="isSearching()" @click="execParentEvent()">
  <div class="card-image">
    <figure class="image is-1by1">
      <img :src="image" alt="Placeholder image">
    </figure>
  </div>
  <div class="card-content">
    <div class="media">
      <div class="media-content">
        <p class="title is-4">{{ name }}</p>
        <p class="subtitle is-6">{{ twitter }}</p>
        <div v-for="z in zokusei" :key="z">
          <b-tag type="is-primary" is-medium rounded>{{ z }}</b-tag>
        </div>
      </div>
    </div>
  </div>
</div>
</transition>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      required: true
    },
    twitter: {
      type: String
    },
    image: {
      type: String
    },
    zokusei: {
      type: Array
    },
    searchName: {
      type: String,
      default: ''
    }
  },

  methods: {
    isSearching:function() {
      if (this.searchName === '' || this.searchName === this.name) {
        return true
      } else if (this.searchName != this.name) {
        return false
      }
    },
    execParentEvent() {
      this.$emit('click')
    }
  }
  // props: ['name', ]
}
</script>

<style lang="scss" scoped>
.card{
    min-width: 194px;
}

.bounce-enter-active {
  animation: bounce-in .5s;
}
.bounce-leave-active {
  animation: bounce-in .5s reverse;
}
@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.5);
  }
  100% {
    transform: scale(1);
  }
}
</style>