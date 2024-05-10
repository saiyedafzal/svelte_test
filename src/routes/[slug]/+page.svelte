<script>
    import { page } from '$app/stores';
    import { onMount } from "svelte";

    let slug = $page.params.slug;
    let product = null;
  
    onMount(async () => {
      const res = await fetch(`https://dummyapi.online/api/products/${slug}`);
      product = await res.json();
    });
  </script>

  <div class="wrapper">
    <div class="product-container">
      <div class="product">
        {#if product}
        <h1>{ product.name }</h1>
        <img
            src={product.featuredImage}
            alt={product.name}
            width={800}
            height={600}
          /> 
        <p>{product.description}</p>
        {/if}
      </div>
    </div>
  </div>
  
  <style>
    .product-container {
      display: flex;
      padding: 0 20px;
      flex-wrap: wrap;
      row-gap: 10px;
      column-gap: 10px;
      align-items: center;
      justify-content: center;
      margin-top: 80px;
    }
  </style>
  