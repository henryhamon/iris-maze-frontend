<script>
	import { onMount } from "svelte";
import { element } from "svelte/internal";
  let api = []
  onMount(async () => {
			const r = await fetch("/csp/iris-maze/api/scoreboard")
				.then(response => response.json())
				.then(data => {
          console.log(data)
					api = data.data
				}).catch(error => {
					console.log(error);
					return [];
				});

	});


</script>

<div class="nes-container with-title is-centered">
  <p class="title">High Score</p>
  <div class="nes-table-responsive is-centered">
  <table class="nes-table is-bordered is-centered" style="width: 97%;">
    <thead>
      <tr>
        <th>Name</th>
        <th>Solution Size</th>
        <th>Mazes Solved</th>
        <th>Score</th>
      </tr>
    </thead>
    <tbody>
      {#each api as element, i}
        <tr>
          <td>
            {#if i === 0}
              <i class="nes-icon trophy is-medium"></i>
            {/if}
            {element.dc_user}
          </td>
          <td>{element.solution_size}</td>
          <td>{element.mazes_solved}</td>
          <td>{element.total_score}</td>
        </tr>

      {/each}
    </tbody>
  </table>
  </div>
</div>
