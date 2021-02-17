<template>
  <div id="homepage">
    <h1>Daten aus Google Spreadsheet</h1>
    <div class="article" v-for="article in articles" :key="article.id">
      <h2> {{ article.headline }} </h2>
      <p> {{ article.content }} </p>
    </div>
  </div>
</template>

<script>
const axios = require('axios')
const _ = require('lodash')
//  your spreadsheet has to be PUBLIC and SHARED with everybody to be accessed this way
//  https://sheets.googleapis.com/v4/spreadsheets/{SPREASHEET_ID}/values/{SHEET_TAB_NAME}!{CELLS}?key={GOOGLE_API_KEY}
   const url = 'https://sheets.googleapis.com/v4/spreadsheets/1tLs9P2bmHKiHlHkh-yvGLjPXzWba_fPz3EssZbpPhmI/values/karriere!A1:D1000?key=AIzaSyBZAwEEqgie7Rfxe0Etb6My-tt5w16rp-M'

export default {
  async asyncData () {
    const response = await axios.get(url)
    const rows = response.data.values
    const properties = rows.shift()
    const articles = []
    for (const i in rows) {
      articles.push(_.zipObject(properties, rows[i]))
    }
    return { articles }
  }
}
</script>

<style>
#homepage {
  padding-top: 10vh;
  max-width: 70vw;
  margin: auto;
}
#homepage h1 {
  padding-bottom: 5vh;
}
#homepage .article {
  padding-bottom: 5vh;
}
</style>