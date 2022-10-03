<script>
  import router from "page"
  import Scoreboard from "./pages/Scoreboard.svelte"
  import Matches from "./pages/Matches.svelte"
  import Maze from "./pages/Maze.svelte"

let page
let params

router('/', () => page = Scoreboard)
router('/matches', () => page = Matches)

router('/maze/:mazeId', (ctx, next) => {
  params = ctx.params
  next()},  () => page = Maze)


router.start()
</script>


<header>
	<nav>
		<ul>
			<li>
				<a  href="/">Scoreboard</a>
			</li>
			<li>
				<a  href="/matches">Matches</a>
			</li>

		</ul>
	</nav>

</header>

<main>
  <svelte:component this={page} params={params} />
</main>


<style>
	header {
		display: flex;
		justify-content: space-between;
	}

	nav {
		display: flex;
		justify-content: center;
		--background: rgba(255, 255, 255, 0.7);
	}


	ul {
		position: relative;
		padding: 0;
		margin: 0;
		height: 3em;
		display: flex;
		justify-content: center;
		align-items: center;
		list-style: none;
		background: var(--background);
		background-size: contain;
	}

	li {
		position: relative;
		height: 100%;
	}

	:global(li.active::before) {
		--size: 6px;
		content: '';
		width: 0;
		height: 0;
		position: absolute;
		top: 0;
		left: calc(50% - var(--size));
		border: var(--size) solid transparent;
		border-top: var(--size) solid var(--accent-color);
	}

	nav a {
		display: flex;
		height: 100%;
		align-items: center;
		padding: 0 1em;
		color: var(--heading-color);
		font-weight: 700;
		font-size: 0.8rem;
		text-transform: uppercase;
		letter-spacing: 0.1em;
		text-decoration: none;
		transition: color 0.2s linear;
	}

	a:hover {
		color: var(--accent-color);
	}



</style>
