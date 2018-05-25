<template>
  <div class="odometer">
    <div class="odometer__inside">
        <span class="odometer__digit">
        <span class="odometer__digit__spacer">{{currentValue || 0}}</span>
        <span class="odometer__digit__inner">
          <span class="odometer__ribbon">
            <span class="odometer__ribbon__inner" :style="getTransformStyle(currentValue)">
              <div class="odometer__value" v-for="(n, index) in 10" :key="index">{{index}}</div>
            </span>
          </span>
        </span>
      </span>
    </div>
  </div>
</template>

<script>
import { SlideYUpTransition } from 'vue2-transitions'

export default {
  name: 'TransitioningNumber',
  props: {
    startValue: {
      type: Number,
      default: 0
    },
    endValue: {
      type: Number,
      default: 5
    },
    duration: {
      type: Number,
      default: 5
    }
  },
  data () {
    return {
      currentValue: this.startValue
    }
  },
  methods: {
    getTransformStyle (value) {
      const translateVal = value >= 0 && value <= 9 ? value * 100 / 10 : 0
      return {
        transform: `translateY(-${translateVal}%)`
      }
    }
  },
  watch: {
    endValue (newVal) {
      this.currentValue = this.endValue
    }
  },
  mounted () {
    setTimeout(() => {
      this.currentValue = this.endValue
    }, 1)
  },
  components: {
    SlideYUpTransition
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.odometer {
  display: inline-block;
  vertical-align: middle;
  position: relative;
  &__inside {
    display: block;
  }
  &__digit {
    display: inline-block;
    vertical-align: middle;
    &__spacer {
      display: inline-block;
      vertical-align: middle;
      visibility: hidden;
    }
    &__inner {
      text-align: center;
      display: block;
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      overflow: hidden;
    }
  }
  &__ribbon {
    display: block;
    &__inner {
      display: block;
      backface-visibility: hidden;
      transition: transform 1s ease-out;
      transform: translateY(0%);
    }
  }
  &__value {
  }
}
</style>
