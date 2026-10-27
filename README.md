# Golang egg for Pelican

Import [`egg-golang.yaml`](egg-golang.yaml) using its raw GitHub URL, create a server, and configure the variables below. Pelican pulls the published Debian image and installs Go automatically.

Upload your Go project or set a GitHub repository and enable pulling. Each startup optionally clones/pulls, builds the package, and runs `/home/container/<executable>`. Pull or build failures stop startup.

| Variable | Default | Description |
| --- | --- | --- |
| `EXECUTABLE` | `server` | Output filename in the server root. |
| `GO_PACKAGE` | `.` | Main-package directory, e.g. `./cmd/api`. |
| `GITHUB_REPO` | Empty | Optional `owner/repo` or GitHub URL; `/tree/dev` selects `dev`. |
| `GITHUB_TOKEN` | Empty | Optional read-only PAT, set in admin startup settings. |
| `PULL_ON_STARTUP` | `0` | Set to `1` to clone/pull before building. |

Public repositories need no token. The first clone requires an empty server directory apart from the generated `.pelican` folder; don't delete or overwrite it. Pulls are fast-forward-only. Branch URLs select that branch; plain repository URLs use the default branch on clone and the current branch afterward. Reinstall to refresh the Go toolchain and startup scripts.

For network services, bind to `0.0.0.0` and read `SERVER_PORT`. Stopping sends SIGINT.
