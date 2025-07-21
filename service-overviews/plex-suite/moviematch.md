# MovieMatch

[Link to Access App](https://moviematch.xfgn.dev/)

[Link to Download App](https://github.com/LukeChannings/moviematch)

MovieMatch connects to your Plex server and gets a list of movies (from any libraries marked as a movie library).

As many people as you want connect to your MovieMatch server and get a list of shuffled movies. Swipe right to 👍, swipe left to 👎.

If two (or more) people swipe right on the same movie, it'll show up in everyone's matches. The movies that the most people swiped right on will show up first.

Moviematch is hosted on Cocoa, as a docker container

{% @github-files/github-code-block url="https://github.com/trentnbauer/agg/blob/205cfc374516886a137f2f0b66dca9c87fa0f740/docker-compose/moviematch.yml" %}

| **Port** | **Purpose** |
| -------- | ----------- |
| 8000     | WebUI       |

| **Host Volume** | **Container Volume** | **Purpose** |
| --------------- | -------------------- | ----------- |
| <p><br></p>     | <p><br></p>          |             |

| **Integration** | **Purpose**                         |
| --------------- | ----------------------------------- |
| Plex            | Reads content from 'Movies' library |
