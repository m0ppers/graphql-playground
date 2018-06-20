# Playground

Repository for the electron playground app.

## Development
```sh
yarn install
yarn start
```

## Production build

```sh
yarn release
```

This will create a `build-electron` folder where you will have the compiled electron app. (The assets will automatically be uploaded to Github if the `GH_TOKEN` env variable is set. See [here](https://www.electron.build/publishing-artifacts) for more.)

## AWS AppSync support

AWS AppSync currently supports API_KEY only.

Create a `.graphqlconfig` config somewhere:

```
{
  "schemaPath": "schema.graphql",
  "extensions": {
    "appSync": {
      "https://my-url.appsync-api.my-region.amazonaws.com/graphql": {
          "region": "my-region",
          "auth": {
            "type": "API_KEY",
            "apiKey": "${env:APPSYNC_API_KEY}"
          }
      }
    },
    "endpoints": {
      "offline": {
        "url": "https://my-url.appsync-api.my-region.amazonaws.com/graphql"
      }
    }
  }
}
```

Then provide the API Key via environment (or using a .env file or or or) and open the directory in GraphQL Playground.
