<template>
  <section class="section">
    <section class="columns is-multiline">
      <div class="column is-4 is-offset-4">
        <div>
          <b-tag style="margin-left: 0.5rem; margin-bottom: 0.25rem;" v-for="vt in vtubers" :key="vt.name" type="is-info">{{ vt.name }}</b-tag>
        </div>
         <b-field>
            <b-input placeholder="Search..."
                type="search"
                icon="magnify"
                icon-clickable
                @icon-click="searchVtuber"
                v-model="searchWord">
            </b-input>
            <p class="control">
                <b-button class="button is-primary" @click="searchVtuber">{{ changeSeachWord }}</b-button>
            </p>
        </b-field>
      </div>
      <div class="column is-12">
        <div class="columns is-multiline card-deck" style="column-gap: 1.5rem;">
            <Vtubercard v-for="vtuber in vtubers"
              :search-name="searchWord"
              :key="vtuber.name"
              :name="vtuber.name" 
              :twitter="vtuber.twitter" 
              :image="vtuber.image"
              :zokusei="vtuber.zokusei">
            </Vtubercard>
        </div>
      </div>
    </section>
  </section>
</template>

<script>
import Card from '~/components/Card'
import Vtubercard from '~/components/Vtubercard'

export default {
  name: 'HomePage',

  data() {
    return {
      searchWord: '',
      vtubers: [
        { name: '月ノ美兎', twitter: '@Tsukinomito', image: 'https://s3-ap-northeast-1.amazonaws.com/liver-icons/400x400/Tsukino_Mito.png' },
        { name: '本間ひまわり', twitter: '@honmahimawari', image: 'https://s3-ap-northeast-1.amazonaws.com/liver-icons/400x400/Honma_Himawari.png' },
        { name: '百鬼あやめ', twitter: '@nakiriayame', image: 'https://user-images.strikinglycdn.com/res/hrscywv4p/image/upload/c_limit,fl_lossy,h_1000,w_500,f_auto,q_auto/1369026/808112_469591.png'
        , zokusei: ['HoloLive', 'かわ余'] },
      ]
    }
  },

  components: {
    Card,
    Vtubercard,
  },

  methods: {
    searchVtuber:function(){

    }
  },

  computed: {
    /* 検索ワードあり：「●●を探す」 検索ワードなし： 「検索」にボタンの文言を変更する */
    changeSeachWord() {
      return this.searchWord != '' ? this.searchWord + 'を探す' : '検索'
    }
  }
}
</script>
