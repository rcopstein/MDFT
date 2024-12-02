# **MDFT - Markdown File Trees**

[![PyPI Version](https://img.shields.io/pypi/v/mdft.svg?style=for-the-badge)](https://pypi.org/project/mdft/)
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-g.svg?style=for-the-badge)](LICENSE)
[![Python Version](https://img.shields.io/pypi/pyversions/mdft.svg?style=for-the-badge)](https://pypi.org/project/mdft/)

## **Overview**
Package for generating file trees in Markdown.

- Define file trees directly in markdown
- In-place update for existing files
- Options for output customization

## **Installation**
MDFT can be installed from PyPI using `pip`:

```bash
pip install mdft
```

## **Usage**
Include a definition line in a `.md` file with the following format:

```html
 <!-- mdft PATH [OPTIONS] -->
```

The file tree will be generated for the specified path and will be inserted in the line that follows the definition. If there is content following the definition line (such as a previous version of the file tree) it will get removed up to the next blank line and replaced with the updated file tree.

MDFT is executed as a module using:

```bash
python3 -m mdft FILE.md
```

### Path
The _Path_ is relative to the `.md` file. The file tree will include all of the files and folders under the specified path, but, by default, will not include an entry for the folder itself (the root folder).


### Options
The _Options_ are comma-separated values that customize the output, but may be ommited.

| Option         | Description                                   |   Type   | Default  |
|:---------------|:----------------------------------------------|:--------:|:--------:|
| filter         | Exclude files listed in `.gitignore`          |   bool   |   True   |
| include_files  | Include files (not just directories)          |   bool   |   True   |
| include_hidden | Include hidden files                          |   bool   |  False   |
| include_root   | Include the root folder in the tree           |   bool   |  False   |
| keep_line      | Keep the definition line in the output file   |   bool   |   True   |
| link           | Create links to the files                     |   bool   |   True   |
| max_depth      | Maximum scan depth from the root folder       |   int    |   None   |

Values for each option are specified in the form of `option=value`, e.g. `max_depth=2`. For `bool` values, you can ommit the value to make it `True`, or prepend a `!` to make it `False`, e.g. `!include_files`.


## **Example**

The following file tree is automatically generated based on the contents of the following definition:

```html
 <!-- mdft src/ include_files,link -->
```

This generates a tree based on the `src/` folder (relative to the current file) including files and generating links for each entry, like follows:

<!-- mdft src/ include_files,link -->
- [mdft/](src/mdft)
	- [converter/](src/mdft/converter)
		- [converter.py](src/mdft/converter/converter.py)
		- [\_\_init\_\_.py](src/mdft/converter/__init__.py)
	- [util/](src/mdft/util)
		- [options.py](src/mdft/util/options.py)
		- [command.py](src/mdft/util/command.py)
		- [blueprint.py](src/mdft/util/blueprint.py)
		- [line.py](src/mdft/util/line.py)
		- [\_\_init\_\_.py](src/mdft/util/__init__.py)
	- [file/](src/mdft/file)
		- [\_\_init\_\_.py](src/mdft/file/__init__.py)
		- [file.py](src/mdft/file/file.py)
	- [\_\_init\_\_.py](src/mdft/__init__.py)
	- [scanner/](src/mdft/scanner)
		- [file\_scanner.py](src/mdft/scanner/file_scanner.py)
		- [\_\_init\_\_.py](src/mdft/scanner/__init__.py)
		- [file\_filter.py](src/mdft/scanner/file_filter.py)
	- [\_\_main\_\_.py](src/mdft/__main__.py)
	- [injector/](src/mdft/injector)
		- [\_\_init\_\_.py](src/mdft/injector/__init__.py)
		- [injector.py](src/mdft/injector/injector.py)

## **Contributing**
Guidelines for contributing to the project:

1. Fork the repository.
2. Create a feature branch (`git checkout -b feature-name`).
3. Commit your changes (`git commit -m 'Add new feature'`).
4. Push to the branch (`git push origin feature-name`).
5. Open a Pull Request.