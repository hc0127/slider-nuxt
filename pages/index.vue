<template>
  <div>
    <h1>Welcome to the homepage</h1>
    <Slider :datas=datas />
  </div>
</template>
<style>
h1 {
  text-align: center;
}
</style>
<script>
export default {
  data() {
    return {
      datas: [{
        img: 'image 1',
        title: 'Unparalleled Quality',
        description: 'Achieveing highly accurate transcription is our number one priority - without compromising speed (1h audio < 60s) while remaining one of the most affordable API providers on the market, add-ons included.'
      }, {
        img: 'image 2',
        title:'100% Security',
        description: `We take our client’s privacy very seriously. Our data hosting is fully compliant with all EU and US regulations, and our portfolio is constantly updated with the latest security add-ons like PII redaction to guarantee full legal compliance.`
      }, {
        img: 'image 3',
        title:'Multilingual Support',
        description: 'Unlike any other provider on the market, our API supports 99 languages for transcription, translation, as well as all of the current and upcoming audio intelligence features.'
      }, {
        img: 'image 4',
        title:'Easy Integration',
        description: 'Our plug-and-play API is compatible with all existing tech stacks and does not require any AI expertise to integrate. Optimized for scalability, our enterprise-grade API is complemented by an intuitive in-app toggle system for the add-ons.'
      }, {
        img: 'image 5',
        title:'Easy Integration',
        description: 'Our plug-and-play API is compatible with all existing tech stacks and does not require any AI expertise to integrate. Optimized for scalability, our enterprise-grade API is complemented by an intuitive in-app toggle system for the add-ons.'
      }],
    }
  }
}
</script>