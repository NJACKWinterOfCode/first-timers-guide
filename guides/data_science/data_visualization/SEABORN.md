#SEABORN
=============

Seaborn is a library for making statistical graphics in Python. It is built on top of matplotlib and closely integrated with pandas data structures. Seaborn aims to make visualization a central part of exploring and understanding data. It's dataset-oriented plotting functions operate on data frames and arrays containing whole data sets and internally perform the necessary semantic mapping and statistical aggregation to produce informative plots.

Some of the functionality that Seaborn offers:

  * A dataset-oriented API for examining relationships between multiple variables
  * Convenient views onto the overall structure of complex datasets
  * Specialized support for using categorical variables to show observations or aggregate statistics
  * Provides a high-level interface for drawing attractive and informative statistical graphics
  * Options for visualizing univariate or bivariate distributions and for comparing them between subsets of data
  * Functions to draw linear regression models

###Installing and getting started

To install the latest release of seaborn, you can use pip:
````sh
    pip install seaborn
````

It’s also possible to install the released version using conda:
```sh
   conda install searborn
```

Alternatively, you can use pip to install the development version directly from github:
```sh
   pip install git+https://github.com/mwaskom/seaborn.git
```

Another option would be to clone the github repository and install from your local copy:
```sh
   pip install
```

####Dependencies

* Python 2.7 or 3.5+

####Mandatory dependencies

* numpy(>=1.9.3)
* scipy(>=0.14.0)
* matplotlib(>=1.4.3)
* pandas(>=0.15.2)

#####Recommended dependencies

* statsmodels(>=0.5.0)

####Testing

To test seaborn, run make test in the root directory of the source distribution. This runs the unit test suite (using pytest, but many older tests use nose asserts). It also runs the example code in function docstrings to smoke-test a broader and more realistic range of example usage.

The full set of tests requires an internet connection to download the example datasets (if they haven’t been previously cached), but the unit tests should be possible to run offline.

##Why seaborn is more preferred than other data visualization libraries?
- - - -
The usage statistics posted on several websites depict that Python data visualization libraries are currently more popular than other data visualization libraries. People prefer this as it allows them to make interactive plots and it is much more flexible than most other popular visualization tools. Seaborn enable users to present huge volumes of data in an easy-to-comprehend visual format. It allows automatic estimation and plotting of linear regression models for different kinds dependent variables and also allows high-level abstractions for structuring multi-plot grids that let you easily build complex visualizations. It also allow data analysts to choose tools color palettes that faithfully reveal patterns in their data and concise control over matplotlib figure styling with several built-in-themes. Most data analysts prefer searborn to visualize data in more appealing way
