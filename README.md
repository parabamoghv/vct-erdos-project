## VCT Erdos Institute Project

TODO: insert description of project

For now, this is a demo of pull-requests.

### getting started

To get started with this repository, we need to set up a reproducible environment. The tool we will use here is Poetry. In a new conda environment (we will use Python 3.10), install Poetry as

```
pip install poetry
poetry install
```

This will install the dependencies of the project into your virtual environment. Now we need to fetch the data from Kaggle. You will first need to get an API authentication token from your Kaggle account (**DO NOT COMMIT THIS TOKEN INTO THE REPO**). Follow https://www.kaggle.com/docs/api#getting-started-installation-&-authentication in order to create an API token and store the generated `kaggle.json` into the recommended location in your filesystem.

Once you have your API token in place, run

```
kaggle datasets download -d ryanluong1/valorant-champion-tour-2021-2023-data -p data/
unzip data/valorant-champion-tour-2021-2023-data.zip -d data/
rm data/valorant-champion-tour-2021-2023-data.zip
```

Now you have the VCT dataset ready to go!
