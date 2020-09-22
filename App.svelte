<script>
  import Face from './Face';
  let say = 'hi';
  setTimeout(() => {
    say = 'bye';
  });
</script>

<style>
  div {
    color: red;
  }
  /* :global(div) {
    background: blue;
  } */
</style>

<div>Say: {say}</div>

<Face size={4} />
<Face size="10" />
<Face />
