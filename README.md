# Website and Lab Exercises for the US Hupo introduction to machine learning short course

This repo contains the Jupyter notebooks that are used as the lab exercises for the machine learning short course at the US Hupo annual conference.

## Contributing Notebooks

Adding content begins with drafting a new Jupyter notebook.
We mostly use [Binder](https://mybinder.org/) to serve our notebooks in an interactive manner for folks to explore.
Binder allows us to add arbitrary dependencies to a Conda environment, making it easier for our students to interact and understand the notebook.

Alternatively, we use [Google Colab](https://colab.research.google.com/) for notebooks that need a GPU.
Two major downsides exist for teaching with Google Colab: the student must have a Google account or be willing to create one and any additional dependencies must be added as an additional cell in the notebook.
The later isn't that big of a deal, but the random code does add to the cognitive load of students already receiving the firehose that is a 1-day introduction to all of ML.

To add a notebook:

1. Add your dependencies to `enironment.yml`.
2. Create and/or update the environment with `make env`.
3. Add any (small-ish) data that you'll need to the `data` directory.
   Even better: Add to the `data` rule in the `Makefile` to automatically download the data in case we ever need to regenerate it.
4. Start up your Jupyter lab instance with `make jupyter`.
   This will activate the conda environment and start Jupyter Lab in the notebooks directory.
5. Add your notebook to the `notebooks` directory, if it is intended to be deployed on Binder.
   Otherwise add them to the `colab` directory.
6. Add a link to your notebook in `docs/index.md`.
   For Binder this is in the following form, replacing `mynotebook` with the name of your actual notebook:
   ```
   https://mybinder.org/v2/gh/wfondrie/ushupo-ml-short-course/main?filepath=notebooks%2mynotebook.ipynb
   ```
   For Colab, again replacing `mynotebook` with the name of your actual notebook:
   ```
   https://colab.research.google.com/github/wfondrie/ushupo-ml-short-course/blob/main/notebooks/mynotebook.ipynb
   ```

Be sure to test your notebook thoroughly - I've learned through experience that folks break them in interesting ways!


## Hiding unnecessary code

As this is an ML short course, rather than an intro to Python, it may be beneficial to hide boilerplate code that doesn't really contribute to folk's understanding.
For this, the `src` directory in this repository acts a Python package.
If your notebook is running on Binder, you can use this package merely by importing `src`:

``` python
import src
```

## Updating the website

The website is built with mkdocs and deployed with GitHub Pages.
We keep it simple, so you should only really ever have to modify `docs/index.md`.
