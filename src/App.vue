<template>
  <div>
    <LikeHeader>
      <h3>はじめまして</h3>
    </LikeHeader>
    <LikeNumber :total-number='number' v-on:my-click="increamentNumber"></LikeNumber>
    <button @click="currentComponent = 'Home'">Home</button>
    <button @click="currentComponent = 'About'">About</button>
    <keep-alive>
      <component :is="currentComponent"></component>
    </keep-alive>
    <div style='padding: 10rem;'>
      <h2>イベントのフォーム</h2>
        <EventTitle v-model="eventData.title"></EventTitle>
        <!-- 同じ意味 -->
        <!-- <EventTitle :value="eventData.title" @input="eventData.title = $event"></EventTitle> -->

        <label for="title">イベントのタイトルの書き換え</label>
        <input id="title" type="text" :value="eventData.title" @input="eventData.title = $event.target.value">
        <pre>{{eventData.title}}</pre>

        <label for="maxNumber">最大人数</label>
        <input id="maxNumber" type="number" v-model.number="eventData.maxNumber">
        <p>{{eventData.maxNumber}}</p>

        <label for="host">イベントのタイトル</label>
        <input id="title" type="text" v-model.trim="eventData.host">
        <pre>{{eventData.host}}</pre>

        <label for="detail">イベントの内容</label>
        <textarea name="" rows="8" cols="80" v-model='eventData.detail'></textarea>
        <pre>{{eventData.detail}}</pre>

        <input type="checkbox" name="" value="" id='isPrivate' v-model='eventData.isPrivate'>
        <label for="isPrivate"></label>
        <p>{{eventData.isPrivate}}</p>

        <p>参加条件</p>
        <input type="checkbox" id='10' name="" value="10代" v-model='eventData.target'>
        <label for="10">10代</label>
        <p>参加条件</p>
        <input type="checkbox" id='20' name="" value="20代" v-model='eventData.target'>
        <label for="20">20代</label>
        <p>参加条件</p>
        <input type="checkbox" id='30' name="" value="30代" v-model='eventData.target'>
        <label for="30">30代</label>
        <p>{{eventData.target}}</p>

        <p>参加費</p>
        <input type="radio" id='free' name="" value="無料" v-model='eventData.price'>
        <label for="free">無料</label>
        <input type="radio" id='paid' name="" value="有料" v-model='eventData.price'>
        <label for="paid">有料</label>

        <p>開催場所</p>
        <select v-model="eventData.location" multiple>
          <option v-for="location in locations" :key='location'>{{location}}</option>
        </select>
        <p>{{eventData.location}}</p>
    </div>
  </div>
</template>
<script>
import LikeHeader from './components/LikeHeader.vue';
import About from './components/About.vue';
import Home from './components/Home.vue';
import EventTitle from './components/EventTitle.vue';

export default {
  data() {
    return {
      number: 14,
      currentComponent: 'Home',
      locations: ['東京', '大阪', '名古屋'],
      eventData: {
        title: "タイトル",
        maxNumber: 0,
        host: '',
        detail: '',
        isPrivate: false,
        target: [],
        price: '無料',
        location: []
      }
    };
  },
  methods: {
    increamentNumber(value) {
      this.number = value;
    }
  },
  components: {
    LikeHeader,
    About,
    Home,
    EventTitle
  }
}
</script>
