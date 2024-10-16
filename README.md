# NRTK EXPLORER

NRTK Explorer is a web application for exploring image datasets. It provides
insights of a image dataset in [COCO][3] format and it evaluate image
transformation and perturbation resilience of object recognition DL models. It
is built using [trame][1] by the [kitware][2] team.

![nrtk explorer screenshot](https://github.com/user-attachments/assets/85c95836-3490-40ec-813d-e6841c540d51)

## Features

- Explore image datasets in COCO format.
- Apply parametrized image degradation (such as blur) to the images.
- Benchmark dataset resilience with a differential PCA|UMAP analysis of the
  embeddings of the images and its transformation.
- Evaluate object detection DL models in both the source images and its
  transformations.
- When possible it will attempt to utilize the user GPU as much as possible to
  speedup its computations.

## Installing

Install it from pypi:

```bash
pip install nrtk-explorer
```

## Usage

```bash
# get some sample data
git clone https://github.com/vicentebolea/nrtk_explorer_datasets.git

# Run the application on given dataset
nrtk-explorer --dataset ./nrtk_explorer_datasets/OIRDS_v1_0/oirds.json
```

![nrtk explorer usage](https://github.com/user-attachments/assets/86a61485-471c-4b94-872e-943cb9da52a1)

Some COCO image datasets available at: https://github.com/vicentebolea/nrtk_explorer_datasets/

## CLI flags and options

- `-h|--help` show the help for the command line options, it inherit trame
  command line options and flags.
- `--dataset` specify the path to a json file describing a COCO
  image dataset. You can specify multiple COCO datasets using a comma `,` as a
  separator. Example usage: `nrtk_explorer --dataset /foo-dir/coco.json, ../bar-dir/baz.json`

## Contribute to NRTK_EXPLORER

```bash
git clone https://github.com/Kitware/nrtk-explorer.git
cd nrtk-explorer
python3 -m venv .venv
source .venv/bin/activate
pip install -U pip
pip install -e '.[dev]'
pytest .
```

[1]: https://trame.readthedocs.io/en/latest/
[2]: https://www.kitware.com/
[3]: https://cocodataset.org/

### Create release

1. Merge `main` to `release` with a _merge commit_.
2. Run "Create Release" workflow with workflow from `release` branch.
3. Merge `release` to `main` with a _merge commit_.
