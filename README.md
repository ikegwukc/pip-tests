# pip-tests

Tutorial on how to setup github repo to be installed with pip

## Tutorial

For this tutorial we will create a python module that can be installed via that tells 2 jokes.


1. The name of this module will be called funniest. So I created a directory called funniest.

2. Inside of the funniest directory create a python file called __init__.py

3. Inside of __init__.py write a function called joke. You can paste in the following code:
```python
def joke():
    print("What has 4 wheels and flies? A garbage truck")
```

4. Next in the main directory create a file called setup.py. Paste the following into setup.py:

``` python
from setuptools import setup

setup(name='funniest',
      version='0.1',
      description='The funniest joke in the world',
      url='http://github.com/ikegwukc/pip-tests',
      author='Kelechi M. Ikegwu',
      author_email='kelechi.ikegwu@gmail.com',
      license='GNU GPL',
      packages=['funniest'],
      #install_requires=['numpy==1.16.2'],
      zip_safe=False)
```

5. Next in the same working directory, run the following command in a terminal:
```bash
pip install -e .
```

6. You can now create a Python file or use an interpeter to import funniest and call the function joke
``` python
import funniest

print(funniest.joke())
```

7. It is possible to add additional Python scripts to files. Add a file called test.py to the funniest directory.

8. Inside of test.py add the following Python
```python
def joke2():
    print("Why is the letter B so cool? Because it’s sitting in the middle of the AC.")

```

9. Inside of __init__.py add the following code to the very first line:
```python
from .test import joke2
```

 __init__.py should look like:
```python
from .test import joke2

def joke():
    print("What has 4 wheels and flies? A garbage truck")

```

10. Reinstall funniest using pip:
```bash
pip install -e .
```

11. Now you can import funniest and call the function joke2 inside of test.py

```python
import funniest

print(funniest.joke2())
```

12. You can also specify dependencies. You can see this in line 11 of setup.py

13. For a more comprehensive tutorial I recommend: https://python-packaging.readthedocs.io/en/latest/index.html
