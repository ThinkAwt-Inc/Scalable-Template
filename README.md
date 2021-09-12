# Scalable

Template Repository to easily get started with CD pipeline for model serving with tensorflow serving and Heroku

# How to Use

- Create an app on your Heroku account (Create Heroku account if you don't have one)

- in your account, go to settings and copy your heroku api key

- on your github repo, go to settings > secrets and add the HEROKU API KEY: `HEROKU_API_KEY` as the key and the api ke you copied from heroku as value

- in the repo, go the `.github/workflows/main.yaml` and uncomment the code

- add your email address to the yaml file and also your app name for example:

  ```yaml
  name: Deploy

  on:
  push:
    branches:
      - main

  jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: akhileshns/heroku-deploy@v3.12.12
        with:
          heroku_api_key: ${{secrets.HEROKU_API_KEY}}
          heroku_app_name: "scalable-example"
          heroku_email: "example@thinkawt.com"
          usedocker: true
  ```

- in the models folder, you can add in your saved tensorflow model (notice the strcture of the default model)

- for every model added in, you must update the `Dockerfile` and `models.conf` file
