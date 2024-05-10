<script>
  import { onMount } from "svelte";
  let products = [];

  onMount(async () => {
    const res = await fetch(`https://dummyapi.online/api/products`);
    products = await res.json();
  });
</script>

<ul class="product-container">
  {#each products as product}
  <a href={product.id}>
    <li>
      <div>
        <h1>
          {product.name.length > 10
            ? product.name.slice(0, 15) + "..."
            : product.name}
        </h1>
        <img
          src={product.thumbnailImage}
          alt={product.name}
          width={400}
          height={300}
        />
      </div>
    </li>
    </a>
  {/each}
</ul>

<style>
  .product-container {
    display: flex;
    padding: 0 20px;
    flex-wrap: wrap;
    row-gap: 10px;
    column-gap: 10px;
    align-items: center;
    justify-content: center;
  }
</style>
