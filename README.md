This repository only exists to demonstrate an issue with
create-react-app-typescript. To set up the demonstration, run:

1. git clone git@github.com:Rovanion/create-react-app-ts-slowdown-demo.git
2. Open three terminals and navigate them all to the newly created
   folder named create-react-app-ts-slowdown-demo.
3. In the first one run: `./node_modules/.bin/tsc --watch --diagnostics`.
4. In the second one run: `npm run start`.
5. Do the manipulation of the repository in the third one as described below:

You are now standing in a repository with two commits. The one at the
HEAD of master includes immutable.js, the one at HEAD~1 does not.

In order to demonstrate the large differences `npm run start` takes to
"compile" the project, open `src/App.tsx` and add a space character
anywhere and save the fil, essentially a NOOP. As you are standing at
the HEAD of master these numbers are _with_ immutable.js.

On my machine such a NOOP takes 0.02s for tsc to compile but the
incremental `npm run start` "compilation" takes 10 seconds.

Then change to the commit without immutable.js, `7ceba58`, with
`git checkout HEAD~1`. Then perform the same addition of a space
character and note how much time it takes for `npm run start` do the
incremental build.

On my machine such a NOOP on `7ceba58` takes 0.02s for tsc and the
incremental build takes 2 seconds.
