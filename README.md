# influxdb-csv-importer
[![Build Status](https://travis-ci.org/escalate/influxdb-csv-importer.svg?branch=master)](https://travis-ci.org/escalate/influxdb-csv-importer)

Import CSV files into InfluxDB

## Installation
Tested with Python 3.6.x on Ubuntu 16.04

If you encounter issues with 3.6.x patch versions of Python, please open a Github issue.

### Requirements
Install needed requirements via pip

#### Production
```
$ pip install -r requirements.txt
```

#### Development
```
$ pip install -r dev-requirements.txt
```

### Run
Run tool from commandline
```
$ ./csvimporter.py
```

## Usage
```
$ ./csvimporter.py --help

Usage: csvimporter.py [OPTIONS] CSVFILE

  Commandline interface for CsvImporter

Options:
  --delimiter TEXT                Delimiter of .csv file (Default: ,)
  --server TEXT                   Server address (Default: localhost)
  --port TEXT                     Server port (Default: 8086)
  --user TEXT                     User for authentication
  --password TEXT                 Pasword for authentication
  --database TEXT                 Database name
  --measurement TEXT              Measurement name
  --timestamp-column TEXT         Name of the column to use as timestamp;
                                  if option is not set,
                                  the current timestamp is used
  --timestamp-format [epoch|datetime]
                                  Format of the timestamp column
                                  used to parse all timestamp
                                  (Default: epoch timestamp);
                                  epoch = epoch / unix timestamp
                                  datetime = normal date and/or time notation
  --timestamp-timezone TEXT       Timezone of the timestamp column
  --locale TEXT                   Locale for ctype, numeric and monetary
                                  values e.g. de_DE.UTF-8
  --date-filter TEXT              Select only rows with a specific date
                                  in the timestamp column for import
                                  e.g. 2020-01-01
  --column-ignorelist TEXT        Ignore a list of columns for import
                                  e.g. col1,col2,col3
  --convert-int-to-float          Convert integer values to float
  --print-columns                 Print all column names in pretty json format
  --print-rows                    Print all rows in pretty json format
  --write-data                    Write data into InfluxDB
  --verbose                       Enable verbose logging output
  --help                          Show this message and exit.
```

## Docker
Build Docker image
```
$ docker build \
    --tag=csvimporter \
    .
```

Run Docker container from built image to print help
```
$ docker run \
    csvimporter

Usage: csvimporter.py [OPTIONS] CSVFILE

  Commandline interface for CsvImporter

Options:
...
```

Run Docker container with additional arguments
```
$ docker run \
    csvimporter \
    file.csv \
    --print-columns \
    --verbose
```

## Dependencies
* [click](https://pypi.python.org/pypi/click)
* [influxdb](https://pypi.python.org/pypi/influxdb)
* [python-dateutil](https://pypi.python.org/pypi/python-dateutil)
* [pytz](https://pypi.python.org/pypi/pytz)

## Helper
Small bash script to run python script within virtualenv
```
$ ./usevenv.sh csvimporter.py
```

## Other Projects
* A commandline tool to convert a CSV file into InfluxDB-compatible JSON written in Ruby [spuder/csv2influxdb](https://github.com/spuder/csv2influxdb)
* A commandline tool to import CSV files into InfluxDB written in GO [jpillora/csv-to-influxdb](https://github.com/jpillora/csv-to-influxdb)
* Another commandline tool to import CSV files into InfluxDB but written in NodeJS [corpglory/csv2influx](https://github.com/CorpGlory/csv2influx)
