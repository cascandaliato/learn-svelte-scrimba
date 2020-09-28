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
  $: question = story[storyIndex];
  $: smileySays = question.end ? finalMessage() : question.smileySays;
  $: buttons = question.buttons;
  function clickHandler(e) {
    if (e.detail.value === 'reset') {
      storyIndex = 0;
      happyIndex = 0;
      showHeader = false;
    } else {
      storyndex += 1;
      happyScore += e.detail.value;
    }
  }

  let name = '';

  $: if (happyScore > 0 && storyIndex === 3) showHeader = true;

  function finalMessage() {
    if (happyScore > 0) {
      return question.end.nice;
    } else if (happyScore < 0) {
      return question.end.mean;
    } else {
      return question.end.neutral;
    }
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
  /* :global(div) {
    background: blue;
  } */

  h1 {
    text-align: center;
    background: #ff3e00;
    font-size: 2em;
    padding: 0.3em 0.6em;
    color: white;
    border-radius: 50px;
  }
  input {
    margin: 1em;
    width: 250px;
    font-family: 'Nunito', sans-serif;
    border: 0;
    outline: 0;
    background: transparent;
    border-bottom: 1px solid black;
    text-align: center;
    font-size: 2em;
  }
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
  <input type="text" bind:value={name} />
  <h1>{name}, {smileySays}</h1>
  <Face {happyScore} size={storyIndex + 1} />
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
