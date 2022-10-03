<script>
	import { onMount } from "svelte";
  let matches = []
  onMount(async () => {
			const r = await fetch("/csp/iris-maze/api/matches/")
				.then(response => response.json())
				.then(data => {
          console.log(data)
					matches = data
				}).catch(error => {
					console.log(error);
					return [];
				});

	});


</script>

<div class="nes-container with-title is-centered">
  <p class="title">Matches by Mazes</p>
  <div class="nes-table-responsive is-centered">
  <table class="nes-table is-bordered is-centered" style="width: 97%;">
    <thead>
      <tr>
        <th>Name</th>
        <th>Matches</th>
      </tr>
    </thead>
    <tbody>
    {#each matches as match (match.maze_id)}
      <tr>
        <td>
          <a  href="/match/{match.maze_id}">{match.maze}</a>
        </td>
        <td>
          <a  href="/match/{match.maze_id}">{match.matches}</a>
        </td>
      </tr>

    {/each}
    </tbody>
  </table>
  </div>
</div>
