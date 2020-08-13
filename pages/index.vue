<template>
  <section class="section">
    <section class="columns is-multiline">
      <div class="column is-4 is-offset-4">
         <b-field>
            <b-input placeholder="Search..."
                type="search"
                icon="magnify"
                icon-clickable
                @icon-click="searchVtuber">
            </b-input>
            <p class="control">
                <b-button class="button is-primary" @click="searchVtuber" >Search</b-button>
            </p>
        </b-field>
      </div>
      <div class="column is-12">
          <Vtubercard></Vtubercard>
      </div>
    </section>
  </section>
</template>

<script>
import Card from '~/components/Card'
import Vtubercard from '~/components/Vtubercard'

export default {
  name: 'HomePage',

  components: {
    Card,
    Vtubercard,
  },

  methods: {
    searchVtuber:function(){

    }
  },

}
</script>
