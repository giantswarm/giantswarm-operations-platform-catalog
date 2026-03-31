# Giant Swarm Issues and Resources

This repository exists exclusively for internal issues as well as documentation and communication.

## Repository Overview

The `content` folder of this repository is served using the static site generator [HUGO](https://gohugo.io/) docs page.
It is set up with the [Google docsy](https://github.com/google/docsy) theme and served at [https://intranet.giantswarm.io/](https://intranet.giantswarm.io/).

For more information on how to add / edit content in Intranet as well as information about the deployment and testing locally checkout [Intranet FAQ](https://github.com/giantswarm/giantswarm/blob/main/content/docs/intranet-faq/_index.md) page.
The full documentation about Docsy is available at https://www.docsy.dev/docs/.

**Note:** Project boards can be found on the [organization level](https://github.com/orgs/giantswarm/projects).

## Notes for Mac M1/M2 users

The docker build takes an unusually long time to perform the Hugo build step, likely due to platform emulation, and can take about 10 minutes before the website is running when performing `docker-compose up` for the first time. Subsequent runs can still take about 5 minutes to build the pages.

It is recommended to run the site using `Hugo` on your local machine, rather than Docker. (See below)

## Running Locally

If you want to run the intranet locally using Hugo on your local machine you must first fetch the git submodules that contain the theme:

```
git submodule update --init --recursive
npm install ; cd themes/docsy ; npm install ; cd ../..
```

Once the submodules are updated you may run `./run-dev-server-with-merge.sh` and navigate to `http://localhost:1313` in your web browser.

## Running locally with docker-compose or podman-compose

This project can be run locally to view the site just like it would be on the server. The Intranet Editor will still try to access the GitHub API, so using it in a local setup may be of limited use for now.

1. Create a `.env` file with the following content (replace the values with your own):
```
ORIGINS=localhost:8081
OAUTH_CLIENT_ID=23456789abcdef123456
OAUTH_CLIENT_SECRET=abcdef1234567890124567890abcdef123456789
GIT_HOSTNAME=
```
2. Run `docker-compose up` or `podman-compose up` (if you have podman installed)
3. Navigate to `http://localhost:8081` in your web browser
