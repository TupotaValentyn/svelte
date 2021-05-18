<script>
  import CoinCard from "./compoents/CoinCard.svelte"

  const BASE_URL = "https://api.coinstats.app/public/v1/coins?skip=0&limit=20";

  let coins = [];

  async function fetchCoins() {
    const response = await fetch(BASE_URL);

    coins = (await response.json()).coins;
  }

  fetchCoins();

</script>

<main>
  <div class="grid">
    {#each coins as coin}
      <CoinCard {coin} />
    {/each}
  </div>
</main>

<style>
  main {
    text-align: center;
    padding: 40px 0;
    margin: 0 auto;
  }
  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }
  .grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
    gap: 30px;
  }
  @media (min-width: 640px) {
    main {
      max-width: 1600px;
      padding: 40px 20px;
    }
  }
</style>
