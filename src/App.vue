<template>
  <div>
    <router-view/>
  </div>
</template>

<script>
import VConsole from 'vconsole'
let vConsole = new VConsole()
const liff = window.liff
console.log(window)
console.log('=================')
console.log('window.navigator.language :: ',window.navigator.language)
console.log(window.navigator.userLanguage)
export default {
  name: 'App',
  data () {
    return {
      profile: {}
    }
  },
  async mounted () {
    this.profile = await this.liffInit()
    console.log(this.profile)
  },
  methods: {
    liffInit () {
      return new Promise((resolve, reject) => {
        liff.init(() => {
          let profile = liff.getProfile()
          resolve(profile)
        }, () => {
          console.log('Error liff')
        })
      })
    }
  }
}
</script>
