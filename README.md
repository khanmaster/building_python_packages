# Building Python Packages

Packages are a way of structuring your Python programs in a form to be reused and included in other programmes.

We will be using some interesting Python functionality with the `__init__.py` file (note not the initialisation of a class...) and the dot notation of using your modules within your package as well as including a file called `setup.py` file to configure your package.

The official documentation on python packaging can be found [here](https://python-packaging.readthedocs.io/en/latest/minimal.html) and should be shared and stored, although can be found easily within a google search.

Build the below structure with the students or a new project with all the files being empty for the time being:

```text
python_package (Root folder)
-- app (folder)
----__init__.py
----fizzbuzz.py
program.py
setup.py
``` 

### The __init__.py file

The __init__.py files are required to make Python treat the directories as containing packages; this is done to prevent directories with a common name, such as string, from unintentionally hiding valid modules that occur later (deeper) on the module search path. In the simplest case, `__init__.py` can just be an empty file, but it can also execute initialization code for the package.

### setup.py

The `setup.py` file is to describe your module and the details regarding it's ownership and distribution. In the early stages of your career it will be unlikely that you'll be creating many but it is worth being aware of as a Python developer!

In it's basic format you can get away with the below as your `setup.py` file:

```python
from setuptools import setup

setup(name="app")
```

There is all sorts of information you could / probably should provide such as:

* version='1.0'
* description='Python app'
* author='Shahrukh@Spartaglobacl'
* author_email='abc.com'
* url='https://www.python.org/sigs/distutils-sig/'

However, in this instance we will keep the `setup.py` as is.

The next step is to utilise pip to install our package, this is to ensure that the Python interpreter is aware of our package and has referenced it into the local library.

* `pip install .` - what we are saying here is install the setup file from the local directory and pip looks for this file as part of it's standard search.

what you should see is something like the below output:

```text
Processing /Users/kierancornwall/workspace/Python_Dev_Curriculum/06_OOP/03_library_modules_&_packages/python_package
Building wheels for collected packages: app
  Running setup.py bdist_wheel for app ... done
  Stored in directory: /private/var/folders/g5/2kx9t92510gd0qx86hmtmc240000gn/T/pip-ephem-wheel-cache-tuo2rz7h/wheels/04/f7/81/9cf56a15687fc12b0a3147b518bbb8fa3cc983102a9dbcfa3d
Successfully built app
Installing collected packages: app
  Found existing installation: app 0.0.0
    Uninstalling app-0.0.0:
      Successfully uninstalled app-0.0.0
Successfully installed app-0.0.0
```

This shows that your app is successfully installed locally and will now be made available in your python library.


### app folder inputs


Within the app folder input the below into the fizzbuzz_oop.py file:

```python
class Fizzbuzz:

    def __init__(self, start_of_range, end_of_range):
        self.fizzrange = range_gen(start_of_range, end_of_range)
        self.fizzbuzz_list = []
        self._fizzbuzz_iterator()

    def _divisible_by(self, num1, num2):
        if num1 % num2 == 0:
            return True
        else:
            return False

    def _fizzbuzz_iterator(self):

        for num in self.fizzrange:
            if self._divisible_by(num, 15):
                self.fizzbuzz_list.append("fizzbuzz")
            elif self._divisible_by(num, 5):
                self.fizzbuzz_list.append("buzz")
            elif self._divisible_by(num, 3):
                self.fizzbuzz_list.append("fizz")
            else:
                self.fizzbuzz_list.append(num)
```


Let's now update our `program.py` file to invoke the fizzbuzz solution:

```python
from app.fizzbuzz import Fizzbuzz

one_to_100 = Fizzbuzz(1, 100)

print(one_to_100.fizzbuzz_list)
```

* `from app.fizzbuzz_oop import Fizzbuzz` within our module importing we should now be able to reference and call our module using the 'dot' notation from our app folder.
```