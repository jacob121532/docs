# Buildkite Documentation [![Build status](https://badge.buildkite.com/b1b9e3ef9d893c087f5e5c0a2d04c258ba393bed2379273f63.svg?branch=main)](https://buildkite.com/buildkite/docs)

The source files for the [Buildkite Documentation](https://buildkite.com/docs).

To contribute, send a pull request! :heart:

## Development

### Before you start

For containerized development, you need Docker and Docker Compose.
Most desktop installations of Docker include Docker Compose by default.
On some platforms, you may need to prefix `docker` commands with `sudo` or add your user to the `docker` group.

For non-containerized development, you need Ruby.
See [`.ruby-version`](.ruby-version) for the current required version
or use [`rbenv`](https://github.com/rbenv/rbenv) to automatically select the correct version of Ruby

### Run the development server

1. Get the source. Run:

   ```bash
   git clone git@github.com:buildkite/docs.git
   cd docs
   git submodule update --init
   ```

2. Build and run the server.

   For non-containerized development, run:

   ```bash
   # Check that you have Xcode Command Line Tools installed - required to build dependencies
   xcode-select -p

   # If not, install them
   xcode-select --install

   # Install dependencies
   bin/setup

   # Start the app
   foreman start
   ```

   Or with Docker, run:

   ```bash
   # Start the app on http://localhost:3000/
   docker-compose up --build
   ```

Open `http://localhost:3000` to preview the docs site.
After modifying a page, refresh to see your changes.

## Updating `buildkite-agent` CLI docs

With the development dependencies installed you can update the CLI docs with the following:


```bash
# Set a custom PATH to select a locally built buildkite-agent
PATH="$HOME/Projects/buildkite/agent:$PATH" ./scripts/update-agent-help.sh
```


## Updating GraphQL API docs

GraphQL API documentation is generated from a local version of the [Buildkite GraphQL API schema](./data/graphql/schema.graphql).

This repository is kept up-to-date with production based on a [daily scheduled build](https://buildkite.com/buildkite/docs-graphql). The build fetches the latest GraphQL schema, generates the documentation, and publishes a pull request for review.

If you need to fetch the latest schema you can either:

- Manually trigger a build on [`buildkite/docs-graphql`](https://buildkite.com/buildkite/docs-graphql); or
- Run the following in your local environment:

```sh
# Fetch latest schema
API_ACCESS_TOKEN=xxx rake graphql:fetch_schema >| data/graphql/schema.graphql

# Generate docs based on latest schema
rake graphql:generate
```


## Linting

We spell-check the docs (American English) and run a few automated checks for repeated words, common errors, and markdown and filename inconsistencies.

You can run most of these checks with `./scripts/vale.sh`.

If you've added a new valid word that showing up as a spelling error, add it to `vale/vocab.txt`.

## Style guide

Our documentation is based on the principles of common sense, clarity, and brevity.

The [style guide](/styleguide/STYLE.md) should provide you a general idea and an insight into using custom formatting elements.

## Search index

**Note:** By default, search (through Algolia) references the production search index.

The search index is updated once a day by a scheduled build using the config in `config/algolia.json`.

To test changes to the indexing configuration:

1. Make sure you have an API key in `.env` like:

    ```env
    APPLICATION_ID=APP_ID
    API_KEY=YOUR_API_KEY
    ```

2. Run `bundle exec rake update_test_index`.


## Updating the navigation

The navigation is split into the following files:

- `nav_graphql.yml`: For the GraphQL API content.
- `nav.yml`: For everything else.

A combined navigation is generated when the application starts.

To update the GraphQL docs, follow the [style guide](/styleguide/STYLE.md#graphql-api-schemas).

Otherwise, to update the general navigation:

1. Edit `nav.yml` with your changes.
1. Restart the application.

## Content keywords

We render content keywords in `data-content-keywords` in the `body` tag to highlight the focus keywords of each page with content authors.

This helps the content team to quickly inspect to see the types of content we're providing across different channels.

Keywords are added as [Frontmatter](https://rubygems.org/gems/front_matter_parser) meta data using the `keywords` key, e.g.:

```md
keywords: docs, tutorial, pipelines, 2fa
```

If no keywords are provided it falls back to comma-separated URL path segments.


## License

See [LICENSE.md](LICENSE.md) (MIT)
