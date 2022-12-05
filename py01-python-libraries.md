Terminology
===========

Terminal and shell means the same thing.

Install Python
==============

Install Python 3.x for Windows, and make sure you tick `Add Python 3.x to PATH`. See below.

![Tick Add Python 3.x to PATH](https://3.bp.blogspot.com/-pQXaSsTBovk/VfqLc2dTvcI/AAAAAAAABNE/SW0e9eEkhzs/s1600/python1.PNG)

Re-install and tick it if you have to. This ensures that you can run `python` and `pip` in your `cmd` terminal.

Edit Python Code
================

Create a folder to keep your python file (eg. fuelwatch.py), use your file manager to go into the folder and open the python file with your favourite text editor (eg. sublime text editor).

Let it contain:

    print('give me fuel, give me fire')

Run Python code
===============

For Windows, launch `cmd` which is a terminal. `cd` into the right folder where `fuelwatch.py` is and run:

    python fuelwatch.py

The workflow is to make changes in your text editor, and continously run `python fuelwatch.py` in the terminal to test that it works.

You should be able to see the output as:

    give me fuel, give me fire

Import library to pull from fuelwatch
=====================================

Have a look at how to use the `requests` library from:

    https://requests.readthedocs.io

Lets add more code in `fuelwatch.py` and attempt to use the `requests` library.

    import requests
    print('give fuel, give me fire')

Try to run the python code, and expect an error that says:

    ModuleNotFoundError: No module named 'requests'

Since `requests` is a third party library, you need to install it first using `pip`. So open your terminal (Not the Python shell!) and run:

    pip install requests

Now try to run `python fuelwatch.py` again, and there will be no complaints.

    import requests
    r = requests.get('https://www.fuelwatch.wa.gov.au/fuelwatch/fuelWatchRSS')
    print(r.content)

You will be using `print` a lot in order to debug your code, in other words, to figure out what value is producing from the code that you write.

Now you can get the string (text) content (formatted as an XML in RSS format) from the URL, now lets install and import another library `feedparser` to work with that RSS content

    import requests
    import feedparser

    response = requests.get('https://www.fuelwatch.wa.gov.au/fuelwatch/fuelWatchRSS', headers={'user-agent': ''})

    feed = feedparser.parse(response.content)
    print(feed)

`feed` is a datastructure type called a 'dictionary', and we will learn about datastructures next week and how to work with them. To see the content of feed we can print then, but it looks unreadable.

Instead we are going to print `feed` with `pprint` (Note that `pprint` is a standard library, so `pip install` is NOT necessary):

    import pprint
    feed = feedparser.parse(response.content)
    pprint.pprint(feed, indent=4)

Or rewritten and imported differently as:

    from pprint import pprint
    feed = feedparser.parse(response.content)
    pprint(feed, indent=4)

The `pprint` to the right of `from` is a module. The `pprint` to the right of `import` is a function. It's too bad that they are named the same that causes some confusion.
