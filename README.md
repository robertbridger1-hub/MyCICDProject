# MyCICDProject
def hello():
    return "Hello, World!"

print(hello())
from app import hello

def test_hello():
    assert hello() == "Hello, World!"
    pytest
wheel
setuptools
from setuptools import setup

setup(
    name="HelloApp",
    version="1.0",
    py_modules=["app"]
)
name: CI/CD Pipeline

on:
  push:
    branches:
      - main

jobs:
  build:

    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - uses: actions/setup-python@v5
        with:
          python-version: "3.11"

      - name: Install dependencies
        run: |
          python -m pip install --upgrade pip
          pip install -r requirements.txt

      - name: Run tests
        run: pytest

      - name: Build application
        run: python setup.py sdist bdist_wheel
