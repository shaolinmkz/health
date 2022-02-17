<script>
</script>

<header>
  <div>
    <a href="/"><img src="/assets/logo.png" alt="logo" /></a>
    <h1>Dashboard</h1>
  </div>
</header>

<style>
  header {
    background-image: linear-gradient(to bottom, #0af, #acfffd 200px);
    display: flex;
    align-items: center;
    justify-content: center;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: 1;
  }

  header > div {
    max-height: 100px;
    max-width: 1440px;
    width: 100%;
    display: flex;
    align-items: center;
    padding: 40px 50px;
  }

  img {
    width: 50px;
    height: 50px;
  }

  a {
    display: inline-block;
    padding-right: 20px;
    border-right: 1px solid rgba(255, 255, 255, 0.2);
  }

  header h1 {
    color: var(--white);
    padding: 0 0 0 20px;
    font-weight: 500;
  }

  @media (max-width: 768px) {
    header > div {
      max-height: 80px;
      padding: 30px 20px;
    }

    header h1 {
      font-size: var(--fs18);
    }
  }

  @media (max-width: 375px) {
    header h1 {
      font-size: 25px;
      padding: 0 0 0 10px;
    }

    img {
      width: 40px;
      height: 40px;
    }

    a {
      display: inline-block;
      padding-right: 10px;
      border-right: 1px solid rgba(255, 255, 255, 0.2);
    }
  }
</style>
