<script>
  import dj from 'dayjs'
  import { readingTimeInMinutes } from '../lib/readingTime'

  export let post
  export let full = false

  function format(date) {
    return dj(date).format('MMM D, YYYY')
  }

  $: created = format(post.date)
  $: modified = format(post.modified)
</script>

<style>
  .attributes {
    display: flex;
    justify-content: space-between;
    font-weight: 400;
    margin-top: -0.125em;
  }
</style>

<div class="attributes">
  <div>
    {created}
    {#if full && created !== modified}<br /> <small>Last update: {modified}</small>{/if}
  </div>
  <div>~ {readingTimeInMinutes(post.content)} min</div>
</div>
