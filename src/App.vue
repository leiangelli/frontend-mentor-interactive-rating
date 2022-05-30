<template>
  <section
    class="card"
    :class="{
      'has-rating': selectedRate && submitted
    }"
  >
    <template v-if="!selectedRate || !submitted">
      <div class="star">
        <img src="@/assets/icon-star.svg" alt="star" />
      </div>

      <h1>How did we do?</h1>

      <p>
        Please let us know how we did with your support request. All feedback is appreciated
        to help us improve our offering!
      </p>

      <ol class="ratings">
        <li 
          v-for="(rate, rateKey) in ratings"
          :key="rateKey"
          @click="selectedRate = rate"
          :class="{
            'is-active': selectedRate === rate
          }"
        >
          {{ rate }}
        </li>
      </ol>

      <button @click="submitted = true">
        SUBMIT
      </button>
    </template>

    <template v-else>
      <img
        src="@/assets/illustration-thank-you.svg"
        alt="thank you"
        class="card__thankyou"
      />

      <span class="card__rate">
        You selected 4 out of 5
      </span>

      <h2>Thank you!</h2>

      <p>
        We appreciate you taking the time to give a rating. If you ever need more support, don’t hesitate to get in touch!
      </p>
    </template>
  </section>
</template>

<style lang="scss">
@import '@/sass/style.scss';
</style>

<script lang="ts">
export default {
  data: () => ({
    ratings: 5,
    selectedRate: 0,
    submitted: false
  })
}
</script>