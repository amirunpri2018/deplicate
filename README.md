<p align="center"><a href="#"><img src="banner.png" alt="deplicate" /></a></p>
<p align="center"><b>Advanced Duplicate File Finder for Python.</b> <i>Nothing is impossible to solve.</i></p>


Table of contents
-----------------

- [Status](#status)
- [Description](#description)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [API Reference](#api-reference)
  - [Properties](#properties)
  - [Methods](#methods)


Status
------

[![Travis Build Status](https://travis-ci.org/vuolter/deplicate.svg?branch=master)](https://travis-ci.org/vuolter/deplicate)
[![Requirements Status](https://requires.io/github/vuolter/deplicate/requirements.svg?branch=master)](https://requires.io/github/vuolter/deplicate/requirements/?branch=master)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/bc7b97415617404694a07f2529147f7e)](https://www.codacy.com/app/deplicate/deplicate?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=vuolter/deplicate&amp;utm_campaign=Badge_Grade)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/vuolter/deplicate/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/vuolter/deplicate/?branch=master)

[![PyPI Status](https://img.shields.io/pypi/status/deplicate.svg)](https://pypi.python.org/pypi/deplicate)
[![PyPI Version](https://img.shields.io/pypi/v/deplicate.svg)](https://pypi.python.org/pypi/deplicate)
[![PyPI Python Versions](https://img.shields.io/pypi/pyversions/deplicate.svg)](https://pypi.python.org/pypi/deplicate)
[![PyPI License](https://img.shields.io/pypi/l/deplicate.svg)](https://pypi.python.org/pypi/deplicate)


Description
-----------

Use **deplicate** to find out all the duplicated files in one or more
directories, you can also scan a bunch of files directly.

**deplicate** is written in Pure Python and requires just a couple
of dependencies to work fine, depending on your system.


Features
--------

- [x] Optimized for speed
- [x] N-tree parsing for low memory consumation
- [x] Multi-threaded (partially)
- [x] Raw drive data access to maximize I/O performances
- [x] xxHash algorithm for fast file identification
- [x] File size and signature checking for quick duplicate exclusion
- [x] Extended file attributes scanning
- [x] Multi-filtering
- [x] Error handling
- [x] Unicode decoding
- [x] Safe from recursion loop
- [x] SSD detection
- [ ] Multi-processing
- [ ] Fully documented
- [ ] PyPy support
- [ ] ~~Exif data scanning~~


Installation
------------

Type in your command shell **with _administrator/root_ privileges**:

    pip install deplicate[full]

In Unix-based systems, this is generally achieved by superseding
the command `sudo`.

    sudo pip install deplicate[full]

The option `full` ensures that all the optional packages will downloaded and
installed as well as the mandatory dependencies.

You can install just the main package typing:

    pip install deplicate

If the above commands fail, consider installing it with the option
[`--user`](https://pip.pypa.io/en/latest/user_guide/#user-installs):

    pip install --user deplicate


Usage
-----

To find the duplicates, import in your python script
the new available module `duplicate` and call its function `find`:

    import duplicate

    entries = ['/path/to/dir1', '/path/to/dir2', '/path/to/file1']

    duplicate.find(entries, recursive=True)

Resulting output is a list of lists of file paths, where each list groups
all the same files:

    [
        ['/path/to/dir1/file1', '/path/to/file1', '/path/to/dir2/subdir1/file1]',
        ['/path/to/dir2/file3', '/path/to/dir2/subdir1/file3']
    ]

> **Note:**
> Resulting file paths are in canonical representation.

> **Note:**
> Resulting lists are sorted in descending order by length.


API Reference
-------------

### Properties

- duplicate.**DEFAULT_MINSIZE**
  - **Description**: Default minimum file size in bytes.
  - **Value**: `102400`

- duplicate.**DEFAULT_SIGNSIZE**
  - **Description**: Default file signature size in bytes.
  - **Value**: `512`

- duplicate.**MAX_BLKSIZES_LEN**
  - **Description**: Default maximum number of cached block size values.
  - **Value**: `128`

### Methods

- duplicate.**clear_blkcache**()
  - **Description**: Clear the internal blksizes cache.
  - **Return**: None.
  - **Parameters**: None.

- duplicate.**find**(`paths, minsize=None, include=None, exclude=None,
    comparename=False, comparemtime=False, compareperms=False, recursive=True,
    followlinks=False, scanlinks=False, scanempties=False, scansystems=True,
    scanarchived=True, scanhidden=True, signsize=None`)
  - **Description**: Find duplicate files.
  - **Return**: Nested lists of paths of duplicate files.
  - **Parameters**:
    - `paths` – Iterable of directory or file paths.
    - `minsize` – _(optional)_ Minimum size of files to include in scanning
      (default to `DEFAULT_MINSIZE`).
    - `include` – _(optional)_ Wildcard pattern of files to include in scanning.
    - `exclude` – _(optional)_ Wildcard pattern of files to exclude
      from scanning.
    - `comparename` – _(optional)_ Check file name.
    - `comparemtime` – _(optional)_ Check file modification time.
    - `compareperms` – _(optional)_ Check file mode (permissions).
    - `recursive` – _(optional)_ Scan directory recursively.
    - `followlinks` – _(optional)_ Follow symbolic links pointing to directory.
    - `scanlinks` – _(optional)_ Scan symbolic links pointing to file.
    - `scanempties` – _(optional)_ Scan empty files.
    - `scansystems` – _(optional)_ Scan OS files.
    - `scanarchived` – _(optional)_ Scan archived files.
    - `scanhidden` – _(optional)_ Scan hidden files.
    - `signsize` – _(optional)_ Size of bytes to read from file as signature
      (default to `DEFAULT_SIGNSIZE`).


------------------------------------------------
###### © 2017 Walter Purcaro <vuolter@gmail.com>
