<script>
  import Face from './Face.svelte';
  import Container from './Container.svelte';
  import Header from './Header.svelte';
  import Buttons from './Buttons.svelte';
  import story from './story';

  let showHeader = false;
  let happyScore = 0;
  let storyIndex = 0;
  let buttons = story[0].buttons;
  $: smileySays = story[storyIndex].smileySays;
  $: buttons = story[storyIndex].buttons;
  function clickHandler(e) {
    storyndex += 1;
    happyScore += e.detail.value;
  }

  // let score = 0;
  // $: if (score < -4) smileySays = 'Wow your score is low!';

  // let showHeader = false;
  // setTimeout(() => {
  //   showHeader = true;
  // }, 1000);

  // let say = false;
  // setTimeout(() => {
  //   say = true;
  // });

  // const buttons = [
  //   { value: 0, text: 'ummmmmm......' },
  //   { value: 1, text: 'I sure do!' },
  //   { value: -2, text: 'gross!' },
  // ];
  // let score = 0;
</script>

<style>
  div {
    color: red;
  }
  /* :global(div) {
    background: blue;
  } */
  :global(*) {
    box-sizing: border-box;
  }
  :global(body, html) {
    margin: 0;
    height: 100vh;
    overflow: hidden;
  }
</style>

<Container>
  <h1>{smileySays}</h1>
  <Face index={2} />
  clickHandler
  <Buttons {buttons} on:click={clickHandler} />

  <!-- <Buttons
    {buttons}
    on:click={(e) => {
      score += e.detail.value;
      storyIndex++;
    }} /> -->

  <!-- <Buttons
    {buttons}
    on:click={(e) => {
      score += e.detail.value;
    }} /> -->

  <!-- <Buttons
    on:click={(e) => {
      showHeader = e.detail;
    }} /> -->

  <!-- <Buttons
    on:show={() => {
      showHeader = true;
    }}
    on:hide={() => {
      showHeader = false;
    }} /> -->

  <!-- <button
    on:click={() => {
      showHeader = true;
    }}>show</button>
  <Buttons>showww</Buttons>
  {#if showHeader}
    <Header />
  {/if}
  {#if say}
    <div>Hi!</div>
  {:else if !say}not saying anything...{/if}
  {#each [2, 1, 0] as faceIndex}
    <Face index={faceIndex} />
  {/each}
  {#each [2, 1, 0] as index}
    <Face {index} />
  {/each}
  <div>Say: {say}</div>

  <Face size={4} />
<Face size="10" />
<Face />
  <Face />
  <Face index={1} />
  <Face index={2} /> -->
</Container>
