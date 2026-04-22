# TESTING

> `jwst` has several test suites to ensure that functionality remains consistent and does not break when code changes.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Running tests for the JWST Calibration Pipeline

`jwst` has several test suites to ensure that functionality remains consistent and does not break when code changes.
In order for a change you make to the code to be accepted and merged, that change must pass existing tests, as well as any new tests you write that cover new functionality.

`jwst` uses `pytest` to define and run tests. To install `pytest` and other required testing tools to your [development environment](./CONTRIBUTING.md#creating-a-development-environment), install `jwst` with the `test` extra:
```shell
pip install -e .[test]
```

To run tests, simply run `pytest`:
```shell
pytest
```

`pytest` recursively searches the given directory (by default `.`) for any files with a name like `test_*.py`, and runs all functions it finds that have a name like `test_*`.

For example, running `pytest` without any arguments will find and run this test from `jwst/associations/tests/test_load_from_asn.py` (along with many others):
```python
from stdatamodels.jwst.datamodels import ImageModel

from jwst.associations.load_as_asn import LoadAsLevel2Asn


def test_lv2_datamodel():
    model = ImageModel()
    model.meta.filename = "modelfile.fits"
    asn = LoadAsLevel2Asn.load(model)
    assert asn.filename == DEFAULT_NAME
    assert asn["program"] == DEFAULT_NAME
    assert asn["target"] == DEFAULT_NAME
    assert asn["asn_pool"] == DEFAULT_NAME
    assert len(asn["products"]) == 1
    assert asn["products"][0]["name"] == "modelfile"
```

To run tests from a specific directory or file, pass the path to `pytest`:
```shell
# only run tests in `jwst/associations/`
pytest jwst/associations/

# only run tests in `jwst/associations/tests/test_load_as_asn.py`
pytest jwst/associations/tests/test_load_as_asn.py
```

To run only specific tests that contain a given string in their name, use `-k <string>`:
```shell
# only run tests with `datamodel` in their name
pytest -k datamodel

# only run the `test_lv2_datamodel` test
pytest

*[truncated — see source for full prompt]*