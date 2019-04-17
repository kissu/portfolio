<template>
  <div class="author">
    <g-image
      alt="Author image"
      class="author__image"
      src="~/assets/images/author.jpg"
      width="180"
      height="180"
      blur="5"
    />

    <h1 v-if="showTitle" class="author__site-title">
      {{ $static.metaData.siteName }}
    </h1>

    <p class="author__intro">
      Hi ! I'm a slav webdev located in Bordeaux, France. I really enjoy being
      part of the JavaScript ecosystem. I'm attending conferences as a speaker
      this year !
    </p>

    <p class="author__links">
      <a href="//twitter.com/kissu_io" target="_blank">twitter</a>
      <a href="//github.com/kissu" target="_blank">github</a>
      <a href="mailto:contact@kissu.io" target="_blank">email</a>
    </p>
  </div>
</template>

<static-query>
query {
  metaData {
    siteName
  }
}
</static-query>

<script>
export default {
  props: ["showTitle"]
};
</script>

<style lang="scss">
.author {
  margin: 0 auto;
  max-width: 550px;
  text-align: center;
  padding: calc(var(--space) / 2) 0;

  &__image {
    border-radius: 100%;
    width: 180px;
    height: 180px;
    margin-bottom: 1em;
  }

  &__intro {
    opacity: 0.8;
  }

  &__site-title {
    font-size: 1.5em;
  }

  &__links {
    margin-top: -0.5em;
    a {
      margin: 0 0.5em;
    }
  }
}
</style>
