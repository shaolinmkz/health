<script>

</script>

<div class="public-wrapper">
  <slot />
</div>

<style>
  .public-wrapper {
    position: relative;
    width: 100%;
    height: 100%;
    overflow: auto;
    padding: 110px 120px 0 120px;
  }

  @media (max-width: 768px) {
    .public-wrapper {
      padding: 110px 15px 0 15px;
    }
  }
</style>
