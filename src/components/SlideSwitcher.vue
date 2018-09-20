<template>
<div>
  <ul class="slide__numbers">
    <li class="slide__numbers-item" v-for="(slide, index) in slides" :key="slide" @click="adressBinding(index)">{{slide}}</li>
  </ul>
</div>
</template>

<script>
export default {
  name: 'SlideSwither',
  props: ['id'],
  data() {
    return {
      slides: ['01', '02', '03', '04', '05', '06', '07', '08', '09'],
      currentAdress: '',
      node: null
    }
  },
  methods: {
    pageFlash() {
      document.addEventListener('click', function(e) {
        if (!!event.target.classList.contains('slide__numbers-item')) {
          if (this.node) {
            this.node.classList.remove('keyboard__active')
          }
          event.target.classList.add('keyboard__active')
          this.node = event.target
        }
      })
    },
    addAdress() {
      window.location.hash = `${this.currentAdress}`
    },
    adressBinding(index) {
      let self = this
      this.id.forEach(function(item, i, arr) {
        if (index === i) {
          self.currentAdress = arr[i]
        }
      })
      this.smoothScroll(this.currentAdress)
      this.pageFlash()
      setTimeout(this.addAdress, 0)
    },
    currentYPosition() {
      if (self.pageYOffset) {
        return self.pageYOffset
      }
    },
    elmYPosition(eID) {
      let elm = document.getElementById(eID)
      let y = elm.offsetTop
      let node = elm
      while (node.offsetParent && node.offsetParent != document.body) {
        node = node.offsetParent
        y += node.offsetTop
      }
      return y
    },
    smoothScroll(eID) {
      let startY = this.currentYPosition()
      let stopY = this.elmYPosition(eID)
      let distance = stopY > startY ? stopY - startY : startY - stopY
      if (distance < 100) {
        scrollTo(0, stopY)
        return
      }
      let speed = Math.round(distance / 100)
      if (speed >= 20) speed = 20
      let step = Math.round(distance / 25)
      let leapY = stopY > startY ? startY + step : startY - step
      let timer = 0
      if (stopY > startY) {
        for (let i = startY; i < stopY; i += step) {
          setTimeout('window.scrollTo(0, ' + leapY + ')', timer * speed)
          leapY += step
          if (leapY > stopY) leapY = stopY
          timer++
        }
        return
      }
      for (let i = startY; i > stopY; i -= step) {
        setTimeout('window.scrollTo(0, ' + leapY + ')', timer * speed)
        leapY -= step
        if (leapY < stopY) leapY = stopY
        timer++
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.slide__numbers {
  list-style: none;
  background-color: #191919;
  color: #fff;
  padding: 0;
  width: 40px;
  text-align: center;
  font-size: 1.2em;
  box-shadow: inset 0px 0px 0px 2px #f99136;
  z-index: 20;
}

.slide__numbers-item {
  margin-bottom: 15px;
  cursor: pointer;
}

.keyboard__active {
  background-color: #f99136;
}

@media only screen and (max-width: 768px) {
  .slide__numbers {
    display: flex;
    width: auto;
  }

  .slide__numbers-item {
    margin: 3px;
  }
}
</style>
