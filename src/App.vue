<template>
  <div id="app">
    <HeaderUSWDSBanner />
    <HeaderUSGS />
    <InternetExplorerPage v-if="isInternetExplorer" />
    <WorkInProgressWarning v-if="checkTypeOfEnv !== '' & !isInternetExplorer" />
    <router-view v-if="!isInternetExplorer" />
    <FooterLinks v-if="!isInternetExplorer & checkIfBarChartIsRendered" />
    <PreFooterCodeLinks v-if="checkIfBarChartIsRendered || isInternetExplorer" />
    <FooterUSGS v-if="checkIfBarChartIsRendered || isInternetExplorer" />
  </div>
</template>

<script>
    import HeaderUSWDSBanner from './components/HeaderUSWDSBanner'
    import HeaderUSGS from './components/HeaderUSGS'
    import WorkInProgressWarning from "./components/WorkInProgressWarning"
    import InternetExplorerPage from "./components/InternetExplorerPage";

    export default {
        name: 'App',
        components: {
            HeaderUSWDSBanner,
            HeaderUSGS,
            WorkInProgressWarning,
            InternetExplorerPage,
            FooterLinks: () => import( /* webpackPrefetch: true */ /*webpackChunkName: "pre-footer-links-visualizations"*/ "./components/FooterLinks"),
            PreFooterCodeLinks: () => import( /* webpackPrefetch: true */ /*webpackChunkName: "pre-footer-links-code"*/ "./components/PreFooterCodeLinks"),
            FooterUSGS: () => import( /* webpackPrefetch: true */ /*webpackChunkName: "usgs-footer"*/ "./components/FooterUSGS")
        },
        data() {
            return {
                isInternetExplorer: false,
              isMobile: false
            }
        },
        computed: {
            checkIfBarChartIsRendered() {
                return this.$store.state.svgRenderedOnInitialLoad;
            },
            checkTypeOfEnv() {
                return process.env.VUE_APP_TIER
            }
        },
        created() {
            // We are ending support for Internet Explorer, so let's test to see if the browser used is IE.
            this.$browserDetect.isIE ? this.isInternetExplorer = true : this.isInternetExplorer = false;
        }
    }
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Source+Sans+Pro&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Source+Sans+Pro:wght@400;700&display=swap');

// Import Colors
$stateFill: #e4e4e3;
$white: rgb(255,255,255);
$axis: rgb(100,100,100);
$lightGray:rgb(237,237,237);
$darkGray: rgb(51,51,51);
$brightBlue: rgb(9,98,178);
$usgsGreen: rgb(51,120,53);
$brightYellow: rgb(255,200,51);

// General CSS
  body{
    margin: 0;
    padding: 0;
    &::-webkit-scrollbar {
      display: none;
    }
  }
  
  #app {
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    width: 100%;
    h1,h2{
      color: black;
      margin: 20px 0;
    }
    h2{
      font-size: 2em;
      margin-top: 80px;
      font-weight: 700;
  
    }
    h3{
      font-size: 1.4em;
      padding-top: .5em;
      font-weight: 700;
      @media screen and (max-width: 600px) {
        font-size: .8em;
    }
    }
    caption,p{
      color: $darkGray;
    }
    .lowlight {
        background: linear-gradient(180deg,rgba(255,255,255,0) 70%, $brightYellow 30%);
        padding: 10px 10px 0 10px;
        line-height: 1.3em;
      }
  }
  caption{
    width: 100%;
    display: block;
    padding: 10px 5px;
    font-style:italic;
    text-align: left;
  }
  .svg-text {
    -webkit-touch-callout: none; /* iOS Safari */
    -webkit-user-select: none;   /* Chrome/Safari/Opera */
    -khtml-user-select: none;    /* Konqueror */
    -moz-user-select: none;      /* Firefox */
    -ms-user-select: none;       /* Internet Explorer/Edge */
    cursor: default;
  }
  *{
    padding:0; margin:0;
  }
  p{
    margin-top:1.5em;
    font-size:16pt;
    line-height:1.5em;
  }

  a{
    text-decoration:none;
    cursor:pointer;
    color: $brightBlue;
    font-weight: 600;
  }

  a:hover{
    text-decoration:underline;
  }

  body{
    font-family: 'SourceSansPro-Regular', Arial, Helvetica, sans-serif;
  }

  figure{
    margin-top: 10px;
  }
  @media screen and (min-width:768px){
    #header h3{
      font-size:1.2em;
      margin:0 0 0 10px;
      padding:0;
    }
  }

  /* aline the usa banner with usgs logo */
  .usa-banner__inner {
    margin-left: 10px;
    padding-left: 5px;
  }
</style>
