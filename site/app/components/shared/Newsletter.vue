<script setup></script>

<template>
  <div class="newsletter-container">
    <h4 class="newsletter__title">NewsLetter</h4>
    <p>Subscribe to my newsletter if you'd like to support.</p>
    <form action="" class="newsletter__form">
      <input type="text" name="" placeholder="Name">
      <input type="email" name="" id="" placeholder="E-mail">
      <textarea name="" id="" cols="30" rows="5" placeholder="Leave a message (Optional)"></textarea>
      <Button text="Subscribe" colourPrimary="#101d2c" colourSecondary="#e6b376" />
    </form>
  </div>
</template>

<style lang="scss" scoped>
.newsletter-container {
  width: 80%;
  margin: 1.5rem auto 0 auto;

  h4 {
    text-align: center;
    font-size: 3rem;
  }

  p {
    text-align: center;
    padding: 1rem 3rem;
  }

  form {
    display: flex;
    flex-direction: column;

    input,
    textarea {
      font-family: inherit;
      font-size: 1.9rem;
      color: #13113a;
      padding: 1.5rem;
      margin-bottom: 2rem;

      &:focus {
        outline: none;
        border-color: #13113a;
      }
    }


    input {
      height: 5rem;
    }


    button {
      align-self: center;
      font-size: 1.6rem;
    }
  }
}
</style>
