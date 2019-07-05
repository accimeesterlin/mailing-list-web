<template>
  <div class="confirmation">
    <h2>Thank you for joing us!!</h2>
    <p>You have successfully subscribed to our mailing list</p>
  </div>
</template>

<script>

export default {
  name: 'confirmation',
};
</script>


<style>

  .confirmation {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    height: 70vh;
  }

  .confirmation p {
    margin-top: 10px;
  }

</style>
