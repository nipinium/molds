<script context="module">
  export async function preload({ params, query }) {
    // the `slug` parameter is available because
    // this file is called [slug].svelte
    const res = await this.fetch(`examples/${params.slug}.json`)
    const data = await res.json()

    if (res.status === 200) {
      return { post: data }
    } else {
      this.error(res.status, data.message)
    }
  }
</script>

<script>
  export let post
</script>

<svelte:head>
  <title>{post.title} - Molds</title>
</svelte:head>

<article>
  <h1>{post.title}</h1>
  <hr />
  {@html post.html}
</article>
