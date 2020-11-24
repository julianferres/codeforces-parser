# codeforces-parser

This is a python script that parses the sample tests from the [Codeforces](http://codeforces.com/) contest problem pages and generates the sample input/output files.

## Requirements:

This tool uses `requests` for loading contest site and `beautifulsoup4` for parsing _HTML_.

## Installation:

[Note] Installation is not necessary, the tool can be run as a script.

CLI tool can be installed by running following command:

```
python setup.py install
```

## Usage

`cfparser --help` prints detailed instructions

```
usage: cfparser.py [-h] [-t TEMPLATE_DIR] type contest [root_dir]

Simple CLI tool for parsing Codeforces contest test samples

positional arguments:
  type                  Type of contest to be parsed (contest or gym)
  contest               ID of the contest
  root_dir              Optional argument root dir, where file structure will
                        be created. By default, this is current dir

optional arguments:
  -h, --help            show this help message and exit
  -t TEMPLATE_DIR, --template_dir TEMPLATE_DIR
                        Optional argument for templates. Expected path to
                        directory containing subdirectory `contest` whose
                        contents is copied to contest root dir, and
                        subdirectory `problem` with template files that are
                        copied to every problem subdirectory. If not provided,
                        no templates are copied.

```

### Example 1: Download contest data

Download data for contest with id 1 ([link](http://codeforces.com/contest/1)) to current directory.

##### Command

```
cfparser contest 1 ./
```

##### Files created on drive

```
.1
├── A1.in
├── A1.out
|
├── B1.in
├── B1.out
```

### Example 2: Using templates

Templates dir can be provided with files that are copied to contest directory and problems subdirectories.

##### Template dir contents

```
templates
├── contest
│   └── CMakeLists.txt
└── problem
    ├── main.cpp
    ├── Makefile
    └── test.sh
```

Example of templates dir containing `CMakeLists.txt` intended to be copied
to contest root dir and `main.cpp`, `Makefile` and `test.sh` script that are copied to every problem.

Download contest 1 to current directory and fill contest and problems dirs with templates provided in `./templates` directory.

##### Usage

```
cfparser 1 contest ./ --template ./templates
```

##### Files created on drive

```
.1
├── A.cpp
├── A1.in
├── A1.out
|
├── B.cpp
├── B1.in
├── B1.out
|
├── Makefile
├── dbg.cpp
├── main.py 


```
