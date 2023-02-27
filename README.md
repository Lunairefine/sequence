# sequence
0xsequence
Sequence: a modular web3 stack and smart wallet for Ethereum chains

Usage
npm install 0xsequence ethers

or

pnpm install 0xsequence ethers

or

yarn add 0xsequence ethers

Packages
0xsequence
@0xsequence/abi
@0xsequence/api
@0xsequence/auth
@0xsequence/config
@0xsequence/deployer
@0xsequence/guard
@0xsequence/multicall
@0xsequence/network
@0xsequence/provider
@0xsequence/relayer
@0xsequence/transactions
@0xsequence/utils
@0xsequence/wallet
Development Environment
Below are notes and instructions on how to get your development environment up and running, and enjoyable.

Install dependencies Run, pnpm install

Workflow -- we use the amazing preconstruct package to handle our monorepo build system.

Local dev -- when you're working on the code in this repository, you can safely run pnpm dev at the root-level, which will link all packages/** together, so that when a local dependency from packages/** is used by another, it will automatically be linked without having to run a build command. Just remember: run pnpm dev anytime you developing in this repo. Note, that when you run pnpm build it will clear the dev environment, so you will need to run pnpm dev again after a build. However, pnpm build should only be used when making a release.

Testing -- to test the system, you can run pnpm test at the top-level or at an individual package-level.

Type-checking -- to typecheck the system you can run pnpm typecheck at any level.

Building -- to compile the project to dist files for a release, run pnpm build at the root-level. Note building packages repeatedly during development is unnecessary with preconstruct. During local development run pnpm dev and when building to make a release, run pnpm build.

Versioning -- this repository uses the handy changesets package for package versioning across the monorepo, as well as changelogs. See Releasing section below.

Releasing to NPM
0xsequence uses changesets to do versioning. This makes releasing really easy and changelogs are automatically generated.

How to do a release
Run pnpm to make sure everything is up to date
Code.. do your magic
Run pnpm changeset to generate a new .changeset/ entry explaining the code changes
Version bump all packages regardless of them having changes or not
Run pnpm i to update the pnpm-lock.yaml.
Commit and submit your changes as a PR for review
Once merged and you're ready to make a release, continue to the next step. If you're not ready to make a release, then go back to step 2.
Run pnpm build && pnpm test to double check all tests pass
Run pnpm version-packages to bump versions of the packages
Run pnpm install so we update our pnpm-lock.yaml file with our newly created version
Commit files after versioning. This is the commit that will be published and tagged: git push --no-verify
Run pnpm release. If the 2FA code timesout while publishing, run the command again with a new code, only the packages that were not published will be published.
Finally, push your git tags, via: git push --tags --no-verify
How to do a snapshot release
NOTE: snapshot release is for dev preview, it's similar to the above, but:

pnpm changeset
pnpm changeset version --snapshot
pnpm changeset publish --tag snapshot
NOTES
Browser tests can be run with pnpm test or, separately pnpm test:server and pnpm test:run
To run a specific test, run pnpm test:only <test-file-basename>, ie. pnpm test:only window-transport
TIPS
If you're using node v18+ and you hit the error Error: error:0308010C:digital envelope routines::unsupported, make sure to first set, export NODE_OPTIONS=--openssl-legacy-provider
LICENSE
Apache-2.0

Copyright (c) 2017-present Horizon Blockchain Games Inc. / https://horizon.io
