# Updating package

```
python -m twine upload dist/*
python setup.py bdist_wheel
python setup.py sdist
pip install -e .
python -m twine upload dist/*
cd ../video-recommender/
git init

```


