# cogran.js

CoGran - A command line tool for combining data of different spatial granularity

**Note: Project is still under development.**


### Installation

To install the cli you need to clone the repository first.

```
$ git clone https://github.com/berlinermorgenpost/cogran.git
```

Now you need to install all dependencies for the application.

```
$ cd /path/to/cogran
$ npm install
```

Using the link command, we install cogran globally:

```
$ npm link
```

### Usage Examples


####  Simple Area Weighting

> for absolute values
```
$ cogran -d -i test/data/base_data/sourcefeatures.geojson -t test/data/base_data/targetfeatures_hierarchical.geojson -o output.geojson --attr Aggr
```

> for relative values
```
$ cogran -d -i test/data/base_data/sourcefeatures.geojson -t test/data/base_data/targetfeatures_hierarchical.geojson --attr Relative --mode arealWeightingRelative -o output.geojson
```

####  Population Weighting

> for absolute values
```
$ cogran -d -i test/data/base_data/sourcefeatures.geojson -t test/data/base_data/targetfeatures_hierarchical.geojson -o output.geojson --attr Aggr --weight population --mode populationWeighting
```

> for relative values
```
$ cogran -d -i test/data/base_data/sourcefeatures.geojson -t test/data/base_data/targetfeatures_nonhierarchical.geojson --attr Relative --weight population --mode populationWeightingRelative -o output.geojson
```

####  Binary Dasymetric Weighting

> for absolute values
```
$ cogran -d -i test/data/base_data/sourcefeatures.geojson -t test/data/base_data/targetfeatures_hierarchical.geojson -o output.geojson --attr Aggr --mode binaryDasymetricWeighting --mask test/data/base_data/binarymask.geojson
```

> for relative values
```
$ cogran -d -i test/data/base_data/sourcefeatures.geojson -t test/data/base_data/targetfeatures_hierarchical.geojson -o output.geojson --attr Relative --mode binaryDasymetricWeightingRelative --mask test/data/base_data/binarymask.geojson
```

####  N-Class Dasymetric Weighting

> for absolute values
```
$ cogran -d -i test/data/base_data/sourcefeatures.geojson -t test/data/base_data/targetfeatures_hierarchical.geojson -o output.geojson --attr Aggr --mode nClassDasymetricWeighting --mask test/data/base_data/nclassmask.geojson
```

> for relative values
```
$ cogran -d -i test/data/base_data/sourcefeatures.geojson -t test/data/base_data/targetfeatures_hierarchical.geojson -o output.geojson --attr Relative --mode nClassDasymetricWeightingRelative --mask test/data/base_data/nclassmask.geojson
```

####  Linear Regression

&nbsp; for absolute values
```
$ cogran -d -i test/data/base_data/sourcefeatures.geojson -t test/data/base_data/targetfeatures_hierarchical.geojson -o output.geojson --attr Aggr --mode linearRegression --mask test/data/base_data/nclassmask.geojson
```


### Options

You can specify these cli options:

* **--aggregate, -a** - Use aggregate mode
* **--disaggregate, -d** - Use disaggregate mode
* **--mode, -m** - Possible values: populationWeighting, populationWeightingRelative, binaryDasymetricWeighting, binaryDasymetricWeightingRealative, nClassDasymetricWeighting, nClassDasymetricWeightingRelative, linearRegression
* **--input, -i** - The path of the input geojson that will be used for aggregation/disaggregation
* **--target, -t** - The path of the target geojson
* **--output, -o** - The path of the output geojson
* **--attr** - The attribute that will be used
* **--weight** - The attribute that is used for weighting
* **--verbose** - Maximum log level
* **--silent** - disable logging

### Tests

To run tests with mocha:
```
$ npm test
```

### Todos

* [ ] Linear Regression
* [ ] bei Linear Regression noch extra Methode f�r Relativ-Werte

### Dependencies

* node.js 5.0 or higher
