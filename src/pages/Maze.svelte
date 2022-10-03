<script>
  import P5 from 'p5-svelte';

	import { onMount } from "svelte";
	import { init } from "svelte/internal";




  const door_icon = 'data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAIAAAACACAYAAADDPmHLAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAADmQAAA5kBQyHEuAAAABl0RVh0U29mdHdhcmUAd3d3Lmlua3NjYXBlLm9yZ5vuPBoAAANwSURBVHic7d2/ThRRGIbx5xgx2JqYaGFirOwsjYWdjVY2XoClnTdhbC3pLC30NmxNYBcMEEnEoEQUJYIigp/Fou4yS1hXZs7MvO8v2WYgO99mnvmz25wUETRZSmkVmDnwmouInayDNURqQQDDPsAuMA9M0xdGRKxUOVsTtDWAw6zzN4jfccxGxLcyZmsCtQCG+QksMngLmY6I1/87WxM4gMNtAB0Gw+hExGZJ+8uikgBSSpPA7ZLe/klJ7ztMAEsUHzpfRUPPpKoCOAe8K31H+WwBXQYfOjsR8TnrVCNwAOVapvjQuRgRe1mn6uMAqrcNzHLgNhIRH3IM4wDq4y2DUTyt4scsB1Bf5yNiteydnCh7B1ZvDkDcydwD9OkC4zwdXznuQZTUKYDr43xvLvGXQAm+BYhzAOIcgDgHIM4BiHMA4hyAOAcgzgGIcwDiHIA4ByDOAYhzAOIcgDgHIM4BiHMA4hyAOAcgzgGIcwDiHIA4ByDOAYhzAOIcgDgHIM4BiHMA4hyAOAcgzgGIcwDiHIA4ByDOAYhzAOIcgDgHIM4BiHMA4hyAOAcgTiWAj8CX3EPUUdsD+ArcAc4CZ4B79JaVtX1tD+B+RDyLnt2ImAIe5B6qTtocwBrweMj2R/SWizXaHUA3IgqX+/1FKSTWBR5FmwP4PubfpLQ5gMvDNqaUJoBLFc9SW20O4GJK6daQ7XeBU1UPU1dtDgBgKqX050qQUroGPMw4T+3UadWwMlwAXqSUngOTwFVgIu9I9dL2AABOAzdyD1FXbb8F2BEcgDgHIM4BiHMA4hyAOAcgzgGIcwDiHIA4ByDOAYhzAOIcgDgHIM4BiHMA4hyAOAcgzgGIcwDiHIA4ByDOAYhzAOIcgDgHIM4BiHMA4hyAOAcgzgGIcwDiHIA4ByDOAYhzAOIcgDgHIM4BiHMA4hyAOAcgzgGIcwDiHIA4ByDOAYirasGIdeDmEf+zWcUgNbYOzPS91qvYaYqIKvZTmpRS0z7AD2CewYM9ExErOYZRWDImp1UOHGjgZUTsZJ2qjwM4HtvAHMWzei3rVCNwAP9umeJZvRARe1mnGpMDONwm0KV4Vm9kneqYOYDeSuJLFM/qpWj6E/II1AL4BHQYPNDdiNjKOlVGbQ1gF1igePl+k3WqGmpDAO8pXr7nIsJLxI/gF7rEFgcurYzaAAAAAElFTkSuQmCC';

  let api = {"maze":{}, "players":[]}
  onMount(async () => {

			api = {"maze":{"map":[["1","0","1","0","0","0","0","1","0","0"],
					["1","0","0","0","0","0","0","0","0","0"],
					["1","0","0","0","0","0","1","0","0","0"],
					["1","0","0","1","0","0","0","0","0","0"],
					["0","0","0","0","0","1","1","0","0","0"],
					["0","0","1","0","0","0","1","0","0","0"],
					["1","0","0","0","0","0","0","0","0","1"],
					["0","0","1","0","0","0","0","0","0","0"],
					["0","0","0","0","1","0","1","1","0","1"],
					["0","0","1","0","1","0","0","1","E","1"]],
					"start_position":[1,0]},"players":[
            {"player_id":"4","dcUser":"player.1","steps":["Down","Down","Down","Down","Down","Down","Right","Right","Down","Right","Right","Right","Right","Right","Down","Down"]},{"player_id":"1","dcUser":"Player-2","steps":["Down","Down","Down","Down","Down","Right Not Allowed","Right Not Allowed","Down","Right","Right","Right Not Allowed","Right Not Allowed","Right Not Allowed","Down","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Right","Right","Down Not Allowed","Right","Right","Right","Right Not Allowed","Right Not Allowed","Down","Down"]},{"player_id":"2","dcUser":"Player 3","steps":["Down","Down","Down","Down","Down","Down","Down","Right Not Allowed","Right Not Allowed","Down","Right","Right Not Allowed","Right Not Allowed","Right Not Allowed","Right Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Right Not Allowed","Right Not Allowed","Down Not Allowed","Right Not Allowed","Right Not Allowed","Right Not Allowed","Right Not Allowed","Right Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Right Not Allowed","Right Not Allowed","Down Not Allowed","Right Not Allowed","Right Not Allowed","Right Not Allowed","Right Not Allowed","Right Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed"]},
            {"player_id":"1","dcUser":"Player-2","steps":["Down","Down","Down","Down","Down","Right Not Allowed","Right Not Allowed","Down","Right","Right","Right Not Allowed","Right Not Allowed","Right Not Allowed","Down","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Right","Right","Down Not Allowed","Right","Right","Right","Right Not Allowed","Right Not Allowed","Down","Down"]},{"player_id":"2","dcUser":"Player 3","steps":["Down","Down","Down","Down","Down","Down","Down","Right Not Allowed","Right Not Allowed","Down","Right","Right Not Allowed","Right Not Allowed","Right Not Allowed","Right Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Right Not Allowed","Right Not Allowed","Down Not Allowed","Right Not Allowed","Right Not Allowed","Right Not Allowed","Right Not Allowed","Right Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Right Not Allowed","Right Not Allowed","Down Not Allowed","Right Not Allowed","Right Not Allowed","Right Not Allowed","Right Not Allowed","Right Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed","Down Not Allowed"]}
          ]}


	});

/*
let clear
$: {
	clearInterval(clear)
	clear = setInterval(turn, videoSpeed)
}
*/

const WALL = "1"
const EXIT = 'E'


const createBoard = (p5, cellsize, maze, exit) => {
  let y = 0;
    maze.map.forEach((cols, row) => {
      cols.forEach((cell, col) => {
        switch (cell) {
          case WALL:
            p5.fill(51);
            p5.rect((col*cellsize), y, cellsize, cellsize);
            break
          case EXIT:
            p5.image(exit, (col*cellsize), y, (exit.height*cellsize/exit.width), cellsize)
            break
          default:
            p5.noFill();
          }
      })
      y = (row + 1) * cellsize;
    });
}

const sketch = (p5) => {
  let cellsize = 0, exit = '', players = [];

  p5.setup = () => {
    if (!api.maze.map) return false;
    exit = p5.loadImage(door_icon);
    cellsize = Math.trunc((p5.windowWidth / api.maze.map[0].length)-10);
    cellsize = (cellsize > 90) ? 50 : cellsize;
    p5.createCanvas(p5.windowWidth, api.maze.map.length * cellsize);
  };

  p5.draw = () => {
    p5.background(250);
    createBoard(p5, cellsize, api.maze, exit);

  };
};

</script>

<P5 {sketch} />
