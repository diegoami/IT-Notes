# Updating package

```
python setup.py bdist_wheel
python setup.py sdist
pip install -e .
python -m twine upload dist/*


```


