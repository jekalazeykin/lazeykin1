<template>
<div class="main__content">
  <div class="slide section" :id="id[0]">
    <div class="first__slide-content">
      <h1 class="first__slide-content-title">{{title}}</h1>
      <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua</p>
    </div>
  </div>
  <div class="slide section" :id="id[1]">
    <div class="second__slide-content">
      <h3>{{inProcess}}</h3>
    </div>
  </div>
  <div class="slide section" :id="id[2]">
    <div class="third__slide-content">
      <div>
        <h1 class="third__slide-content-title">CO<span class="color-letters">LL</span>IDER</h1>
        <h3 class="third__slide-content-body">{{thiirdSlideTitle}}</h3>
      </div>
    </div>
  </div>
  <div class="slide section" :id="id[3]">
    <div class="fourth__slide-content">
      <div class="fourth__slide-content-left">
        <div>
          <h1 class="fourth__title">{{fourthSlideTitle}}</h1>
          <p>Info your property is worth in the <br>
            <span class="color-text">$5 - 6.2M range</span><br> Colider has identified 25 most<br> likely buyers</p>
        </div>
      </div>
      <div class="fourth__slide-content-right">
        <div class="button__container">
          <button type="button" name="button" class="comparables">Comparables</button>
          <button type="button" name="button" class="sell">Sell with us?</button>
        </div>
      </div>
    </div>
  </div>
  <div class="slide section" :id="id[4]">
    <div class="fivth__slide-content">
      <form class="form" method="post" v-if="showForm">
        <label for="ask">Asking price</label>
        <div class="input__ask">
          <input type="text" class="ask" required>
        </div>
        <div class="file-upload">
          <label>
          <input type="file" name="file">
          <span>Attach Rent Roll & Exprenses</span>
          </label>
        </div>
        <label for="comment">Comments</label>
        <div class="input__comment">
          <textarea id="comment" required></textarea>
        </div>
        <div class="button-container">
          <button type="submit" name="button" @click.prevent="submitData">Submit</button>
        </div>
      </form>
      <div v-else>
        <p>Your data has been sent successfully</p>
      </div>
    </div>
  </div>
  <div class="slide section" :id="id[5]">
    <div class="sixth__slide-content">
      <h3>{{inProcess}}</h3>
    </div>
  </div>
  <div class="slide section" :id="id[6]">
    <div class="seventh__slide-content">
      <div>
        <h2>WE HAVE RESEIVED YOUR</h2>
        <ul class="list">
          <li class="list__item" v-for="list in seventhList" :key="list">{{list}}</li>
        </ul>
      </div>
    </div>
  </div>
  <div class="slide section" :id="id[7]">
    <div class="eighth__slide-content">
      <div>
        <h2 class="eighth__title">PROPERTY SALE STATUS REPORT</h2>
        <ul class="eighth__list">
          <li class="eighth__list_item"><span class="big-size"><b>45</b><span class="color__text">575</span></span><br>Lorem ipsum dolor sit</br>
          </li>
          <li class="eighth__list_item"><span class="big-size"><b>5</b><span class="color__text">755</span></span><br>Lorem ipsum dolor sit amet, consectetur adipisicing elit</br>
          </li>
          <li class="eighth__list_item"><span class="big-size"><b>2</b><span class="color__text">745</span></span><br>Lorem ipsum dolor sit amet</br>
          </li>
          <li class="eighth__list_item"><span class="big-size"><b>5</b><span class="color__text">755</span></span><br>Lorem ipsum</br>
          </li>
        </ul>
      </div>
    </div>
  </div>
  <div class="slide section" :id="id[8]">
    <div class="ninth__slide-content">
      <h3>{{inProcess}}</h3>
    </div>
  </div>
  <SlideSwitcher :id="id" class="slide__swither"></SlideSwitcher>
</div>
</template>

<script>
import SlideSwitcher from '@/components/SlideSwitcher';

export default {
  name: 'Home',
  components: {
    SlideSwitcher
  },
  data() {
    return {
      title: 'THE FIRST VIRTUAL REAL ESTATE MARKETPLACE',
      inProcess: 'Work in progress',
      thiirdSlideTitle: 'Analyzing Data',
      fourthSlideTitle: 'BASED ON PROVIDED',
      seventhList: ['Property info', 'Signed Commission Agreement', 'Rent roll & exprenses',
        'Your will receive your first Property Sale Report in 7 days'
      ],
      id: ['slide1', 'slide2', 'slide3', 'slide4', 'slide5', 'slide6', 'slide7', 'slide8', 'slide9'],
      showForm: true
    }
  },
  methods: {
    submitData() {
      let self = this
      setTimeout(function() {
        return self.showForm = false
      }, 2000)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import url('https://fonts.googleapis.com/css?family=Fjalla+One');
.main__content {
  margin: 11vh 0 13vh;
  color: #fff;
  border: 2px solid #e236f9;
}

.slide__swither {
  position: fixed;
  right: 5vw;
  top: 25vh;
}

.slide {
  background-color: #191919;
  position: relative;
  height: 100vh;
  border-bottom: 3px solid red;
}

.first__slide-content {
  width: 40vw;
  position: absolute;
  top: 20vh;
  left: 15vw;
}

.first__slide-content>p {
  max-width: 230px;
}

.first__slide-content-title {
  position: relative;
  z-index: 5;
}

.first__slide-content-title::before {
  content: "";
  display: block;
  position: absolute;
  top: -50px;
  left: -50px;
  z-index: -10;
  width: 130px;
  height: 130px;
  background-color: #eac02a;
}

.second__slide-content,
.sixth__slide-content,
.ninth__slide-content {
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.third__slide-content {
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;

}

.third__slide-content-title {
  font-family: 'Fjalla One', sans-serif;
  font-size: 4em;
  margin: 0 0 5px;
}

.third__slide-content-body {
  margin: 0;
  text-align: center;
}

.color-letters {
  color: #eac02a;
}

.fourth__slide-content {
  height: 100%;
  display: flex;
}

.fourth__slide-content-left {
  display: flex;
  align-items: center;
  padding-left: 10vw;
  width: 50%;

}

.fourth__slide-content-right {
  background-color: #4c4b4a;
  width: 50%;
  position: relative;
  text-align: center;
}

.button__container {
  position: absolute;
  bottom: 15vh;
  left: 25%;
}

.fourth__title {
  position: relative;
  width: 13vw;
  z-index: 5;
}

.fourth__title::before {
  content: "";
  display: block;
  position: absolute;
  top: -50px;
  left: -50px;
  z-index: -10;
  width: 130px;
  height: 130px;
  background-color: #eac02a;
}

.color-text {
  color: #eac02a;
}

.comparables {
  background-color: #eac02a;
  color: #fff;
  border: none;
  cursor: pointer;
  height: 25px;
}

.sell {
  background: none;
  border: 1px solid #eac02a;
  cursor: pointer;
  height: 25px;
  color: #fff;
}

.fivth__slide-content {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}

.form {
  max-width: 320px;
}

.file-upload {
  position: relative;
  overflow: hidden;
  width: 250px;
  height: 20px;
  background: none;
  border: 1px solid #ada9a6;
  padding: 8px 4px;
  color: #fff;
  text-align: center;
  opacity: 0.3;
}

.file-upload input[type="file"] {
  display: none;
}

.file-upload label {
  display: block;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  cursor: pointer;
}

.file-upload span {
  line-height: 36px;
}

textarea {
  width: 280px;
  height: 80px;
  padding: 10px;
  background-color: #191919;
  border: 1px solid #ada9a6;
}

.ask {
  width: 250px;
  height: 20px;
  padding: 8px 4px;
  background-color: #191919;
  border: 1px solid #ada9a6;
}

.input__ask,
.file-upload,
.input__comment {
  margin-bottom: 20px;
}

.button-container {
  text-align: center;
}

.button-container>button {
  width: 120px;
  background-color: #eac02a;
  color: #fff;
  border: none;
  height: 30px;
  cursor: pointer;
}

.seventh__slide-content {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
  background-color: #4c4b4a;
}

.list {
  list-style: none;
}

.list__item {
  margin-bottom: 15px;
  position: relative;
}

.list__item::before {
  content: url(../assets/checked.svg);
  position: absolute;
  left: -20px;
}

.eighth__slide-content {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}

.eighth__list {
  list-style: none;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  padding: 0;
}

.eighth__list_item {
  width: 150px;
  margin: 10px 0 15px 30px;
}

.big-size {
  font-size: 2.2em;
}

.color__text {
  color: #eac02a;
}

.eighth__title {
  text-align: center;
}

@media only screen and (max-width: 768px) {

  .slide__swither {
    right: 20vw;
    top: 9vh;
    z-index: 5;
  }

  .first__slide-content {
    width: auto;
  }

  .fourth__slide-content {
    flex-wrap: wrap;
  }

  .fourth__slide-content-left {
    width: 100%;
  }

  .fourth__slide-content-right {
    width: 100%;
  }
}
</style>
