<template>
  <div id="component-infographic">
    <div class="grid-infographic-1">Each dot on the map above is a <em>streamgage</em></div>
    <div class="grid-infographic-2"> main gage graphic ...................................<br><br><br></div>
    <div class="grid-infographic-3">first water line ...................................................................................</div>
    <div class="grid-infographic-4">That data is critical for water management</div>
    <div class="grid-infographic-5">The National Streamgaging program is funded by <em>Congress</em></div>
    <div class="grid-infographic-6">image of congress</div>
    <div class="grid-infographic-7">and over 1,400 state and local partner agencies.</div>
    <div class="grid-infographic-8">It's managed by the USGS, the U.S. Geological Survey, which has been
      operating streamgages fro the last 130 years.</div>
    <div class="grid-infographic-9">image small gage on post</div>
    <div class="grid-infographic-10">The story of streamgages tells the story of the evolving water needs of the the nation.</div>
    <div class="grid-infographic-11">second water line .............................................................................</div>
    <div class="grid-infographic-12">image - larger gage.</div>
  </div>
</template>

<script>
export default {
  name: 'Infographic'
}
</script>

<style scoped lang="scss">
#component-infographic {
  display: grid;
  grid-template-columns: 1fr 2fr 2fr 1fr;
  .grid-infographic-1 {
    background-color: #97d4ea;
    grid-column: 2;
    grid-row: 1;
    justify-self: start;
  }
  .grid-infographic-2 {
    background-color: #04c585;
    grid-column: 2 / 3;
    grid-row: 2 / 5;
    justify-self: start;
    z-index: 2;
  }
  .grid-infographic-3 {
    background-color: #0076d6;
    grid-column: 1 / 4;
    grid-row: 3;
    justify-self: start;
    z-index: 1;
  }
  .grid-infographic-4 {
    background-color: #4AAE9B;
    grid-column: 2;
    grid-row: 5;
    justify-self: start;
  }
  .grid-infographic-5 {
    background-color: #4aa2ae;
    grid-column: 2;
    grid-row: 6;
    justify-self: start;
  }
  .grid-infographic-6 {
    background-color: #79ae4a;
    grid-column: 2 / 3;
    grid-row: 7;
    justify-self: start;
  }
  .grid-infographic-7 {
    background-color: #aea94a;
    grid-column: 3;
    grid-row: 8;
    justify-self: start;
  }
  .grid-infographic-8 {
    background-color: #744aae;
    grid-column: 2;
    grid-row: 9;
    justify-self: start;
  }
  .grid-infographic-9 {
    background-color: #ae814a;
    grid-column: 4;
    grid-row: 10;
    justify-self: start;
  }
  .grid-infographic-10 {
    background-color: #8bae4a;
    grid-column: 2 / 3;
    grid-row: 11;
    justify-self: start;
    z-index: 2;
  }
  .grid-infographic-11 {
    background-color: #4a60ae;
    grid-column: 1 / 4;
    grid-row: 11;
    justify-self: start;
    z-index: 1;
  }
  .grid-infographic-12 {
    background-color: #54ae4a;
    grid-column: 1;
    grid-row: 12;
    justify-self: start;
  }

}
</style>