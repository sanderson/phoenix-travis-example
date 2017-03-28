# Sample Phoenix App Showing How to Use Nanobox with Travis CI

This repo is a companion to the article, [Continuous Integration with Travis CI & Nanobox](https://content.nanobox.io/continuous-integration-with-travis-ci-nanobox) showing how to use Nanobox in your Travis CI workflow.

## Nanobox
[Nanobox](https://nanobox.io) is a "micro-platform" that builds and runs your app anywhere - your local machine, a CI server, or in production.

## Travis CI
[Travis CI](https://travis-ci.org) is a continuous integration platform that allows you to thoroughly test code as it moves through your development/deployment workflow.

## Running This App Locally
### Download & Install Nanobox
Create a Nanobox account (it's free), then [Download & Install Nanobox](https://dashboard.nanobox.io/download).

### Clone This Repo
```sh
# clone the code
git clone https://github.com/sanderson/phoenix-travis-example.git

# cd into the project directory
cd phoenix-travis-example
```

### Add a Convenient Way to Access the App
Nanobox provides a simple way to add DNS aliases for apps running locally, so you can easily access them from a browser.

```sh
nanobox dns add local phoenix.dev
```

### Start Your Local Dev Environment
Nanobox will spin up a virtualized local dev environment isolated from your host machine.

```sh
nanobox run
```

This will drop you into a console inside your Nanobox container.

### Setup Phoenix
To get everything in place, you just need to install dependencies and seed your database. From inside your Nanobox console, run:

```sh
# install dependencies
mix deps.get

# seed the database
mix ecto.create && mix ecto.migrate

# install Node.js dependencies
npm install
```

### Run the App
With dependencies in place and data seeded, run the app with the following command (in the Nanobox console):

```sh
mix phoenix.server
```

Now you can visit [`phoenix.dev:4000`](http://phoenix.dev:4000) from your browser.

## Using the App with Travis CI
Travis CI uses settings in the `.travis.yml` to build a testing environment and run tests. If tests are successful, this repo is configured to deploy to a live app with Nanobox.

This app is also configured to include the [Travis CLI](https://github.com/travis-ci/travis.rb) in the local dev environment.
