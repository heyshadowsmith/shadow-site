<template>
  <Layout>
    <h1>
      Hello, my name is Shadow Smith 
    </h1>
    <p>I am a serial learner and software engineer that believes opportunities for discovery and growth are limitless with the power of current web technologies, and as a result, I have developed an insatiable passion for creatively solving problems and inspiring others to do the same.</p>
  </Layout>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>

<script>
import { TwitterIcon, GithubIcon, CodepenIcon, LinkedinIcon } from 'vue-feather-icons'
import Logo from '~/components/Logo.vue'

export default {
  components: {
    TwitterIcon,
    GithubIcon,
    CodepenIcon,
    LinkedinIcon,
    Logo
  },
  data() {
    return {
      logoColor: 'bright'
    }
  },
  metaInfo() {
    return {
      title: this.description,
      meta: [
        { key: 'description', name: 'description', content: 'A theme for static site documentation based on Gridsome, ready to deploy to Netlify in one click.' }
      ]
    }
  },
  mounted() {
    if (process.isClient) {
      this.logoColor = localStorage.getItem('theme')
    }
  }
}
</script>
