# AutoRA Template

## Quickstart Guide

Install this in an environment using your chosen package manager. In this example we are using virtualenv

Install:
- python (3.8 or greater): https://www.python.org/downloads/
- virtualenv: https://virtualenv.pypa.io/en/latest/installation.html

Create a new virtual environment:
```shell
virtualenv venv
```

Activate it:
```shell
source venv/bin/activate
```

Use `pip install` to install the current project (`"."`) in editable mode (`-e`) with dev-dependencies (`[dev]`):
```shell
pip install -e ".[dev]"
```

## Add your contribution 
Your autora-subpackage should include (1) your code implementing in the respective folder of src/autora/*, 
(2) **tests** for your contribution, and (3) respective **documentation**.

### Adding your code implementation
Add your code implementation to src/autora/theorist, src/autora/experimentalist or src/autora/experiment_runner. You can create new categories if none of them seems fitting.

### Adding tests
You should also add tests. These can be [doctests](https://docs.python.org/3/library/doctest.html) or as test cases in `tests/test_your_contribution_name.py`. 

### Adding documentation
***Whenever possible stick to the templates provided to ensure coherent documentation***
- You may document your contribution in `docs/index.md`. You can also add new pages in the `docs` folder
  - It is recommended to include at least a `index.md` file with an overview and a `quick_start_guide.md` file, where the setup is explained.
  - It is also very useful for users to include at least one example in form of a jupiter notebook. If you want to include a basic example, please use the basic_usage.ipynb file. You can add more examples (if possible, please replace the names of the additional_example to something more descriptive)
- Update the `mkdocs.yml` file to reflect structure of the documentation. You can add additional pages and examples here.
- Update the README.md file 

### Spicy Documentation:

You can use the github actions in this version of the template to quickly generate streamlined documentation:
#### Build index and quick-start from toml file:
- after updating the toml file use the build-pages-from-toml.yml github-action to auto generate an index and quick-start file
- this creates a pull request with the changes
- after merging the pull request you can customize the index.md and quick-start.md file
#### Building code references
- after adding code to the src file you can use the build-code-references.yml action to generate static markdown code from the docstrings
#### Generating the README.md
- instead of updating the README.md file you can update the README-src.md file and use include statements to include parts of your other documentation. This makes the documentation more coherent.
- Use the build-reamde.yml action to generate the README.md file from README-src.md

***All the above actions are customizable in the respective yml files to use different src or output files***


## Add new dependencies 

In pyproject.toml add the new dependencies under `dependencies`

Install the added dependencies
```shell
pip install -e ".[dev]"
```

## Publishing the package

Update the metadata under `project` in the pyproject.toml file to include name, description, author-name, author-email and version.
Also, update the URL for the repository under `project.urls`.

### Publishing with GitHub actions
**You'll need a secret with a piPY token for this to work with the name PYPI_API_TOKEN**
To automate the publishing process for your package, you can use a GitHub action instead of Twine:
- Add the GitHub action to the `.github/workflows` directory: For example, you can use the default publishing action:
  - Navigate to the `actions` on the GitHub website of your repository.
  - Search for the `Publish Python Package` action and add it to your project
- Create a new release: Click on `create new release` on the GitHub website of your repository.
- Choose a tag (this is the version number of the release. If you didn't set up dynamic versioning it should match the version in the `pyproject.toml` file)
- Generate release notes automatically by clicking `generate release`, which adds the markdown of the merged pull requests and the contributors.
- If this is a pre-release check the box `set as pre-release`
- Click on `publish release`

## Workflows
...
