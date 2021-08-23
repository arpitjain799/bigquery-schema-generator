# Changelog

* Unreleased
* 1.4.1 (2021-08-23)
    * Add documentation for the `input_format='dict'` option.
    * Add additional inpout format 'json' and 'dict' test cases.
    * Maintenance release, no functional change in core code.
* 1.4 (2020-12-09)
    * Add 'dict' as a third `input_format` when `SchemaGenerator` is used as a
      library. This can be useful when the data has already been transformed
      into a list of native Python `dict` objects (see #58, thanks to
      ZiggerZZ@).
    * Expand the pattern matchers for quoted integers and quoted floating point
      numbers to be more compatible with the patterns recognized by `bq load
      --autodetect`.
    * Add Table of Contents to READMD.md. Add usage info for the
      `schema_map=existing_schema_map` and the `input_format='dict'` parameters
      in the `SchemaGenerator()` constructor.
* 1.3 (2020-12-05)
    * Allow an existing schema file to be specified using
      `--existing_schema_path` flag, so that new data can be merged into it.
      See #40, #57, and #61.
      (Thanks to abroglesc@ and bozzzzo@).
* 1.2 (2020-10-27)
    * Print full path of nested JSON elements in error messages (See #52;
      thanks abroglesc@).
* 1.1 (2020-07-10)
    * Add `--ignore_invalid_lines` to ignore parsing errors on invalid lines
      and continue processing. Fixes
      [#49](https://github.com/bxparks/bigquery-schema-generator/issues/49).
    * Add GitHub actions for automated tests and flake8 validation.
    * Add package `__version__` string.
    * Update setup.py, no longer need to convert README.md markdown to RST.
* 1.0 (2020-04-04)
    * Fix `--sanitize_names` for recursive RECORD fields (Thanks riccardomc@,
      see #43).
    * Clean up how unit tests are run, trying my best to figure out
      Python's convolution package importing mechanism.
    * Add GitHub Actions continuous integration pipelines with flake8 checks and
      automated unit testing.
* 0.5.1 (2019-06-17)
    * Add `--sanitize_names` to convert invalid characters in column names and
      to shorten them if too long. (See #33; thanks jonwarghed@).
* 0.5 (2019-06-06)
    * Add input and output parameters to run() to allow the client code using
      `SchemaGenerator` to redirect the input and output files. (See #30).
    * Remove fields with incompatible types (or other errors) from the generated
      schema, instead of picking the type of the first encounter. (See #31).
    * Improve internal data validation handling, reserving exceptions for
      programming errors only.
* 0.4 (2019-03-06)
    * Support CSV input files using `--input_format` flag. Preserve
      the ordering of fields in the schema file for CSV.
    * Implement `--infer_mode` flag for CSV files so that fields that are
      present in all input records are marked as `REQUIRED` in the schema
      (Thanks korotkevics@, see #28).
* 0.3.2 (2019-02-24)
    * Add `--quoted_values_are_strings` flag to force quoted values (integers,
      floats, booleans) to be interpreted as a `STRING`. (Thanks de-code@,
      see #22).
* 0.3.1 (2019-01-18)
    * Infer integers that overflow signed 64-bits to be `FLOAT` for
      consistency with `bq load`. (Fixes #18)
    * Support 'UTC' suffix in TIMESTAMP fields, in addition to 'Z'. (Fixes #19)
* 0.3 (2018-12-17)
    * Tighten TIMESTAMP and DATE validation (thanks jtschichold@).
    * Inspect the internals of STRING values to infer BOOLEAN, INTEGER or FLOAT
      types (thanks jtschichold@).
    * Handle conversion of these string types when mixed with their non-quoted
      equivalents, matching the conversion logic followed by 'bq load'.
* 0.2.1 (2018-07-18)
    * Add `anonymizer.py` script to create anonymized data files for
      benchmarking.
    * Add benchmark numbers to README.md.
    * Add `DEVELOPER.md` file to record how to upload to PyPI.
    * Fix some minor warnings from pylint3.
* 0.2.0 (2018-02-10)
    * Add support for `DATE` and `TIME` types.
    * Update type conversion rules to be more compatible with **bq load**.
        * Allow `DATE`, `TIME` and `TIMESTAMP` to gracefully degrade to
          `STRING`.
        * Allow type conversions of elements within arrays
          (e.g. array of `INTEGER` and `FLOAT`, or array of mixed `DATE`,
          `TIME`, or `TIMESTAMP` elements).
        * Better detection of invalid values (e.g. arrays of arrays).
* 0.1.6 (2018-01-26)
    * Pass along command line arguments to `generate-schema`.
* 0.1.5 (2018-01-25)
    * Updated installation instructions for MacOS.
* 0.1.4 (2018-01-23)
    * Attempt #3 to fix exception during pip3 install.
* 0.1.3 (2018-01-23)
    * Attempt #2 to fix exception during pip3 install.
* 0.1.2 (2018-01-23)
    * Attemp to fix exception during pip3 install. Didn't work. Pulled.
* 0.1.1 (2018-01-03)
    * Install `generate-schema` script in `/usr/local/bin`
* 0.1 (2018-01-02)
    * Iniitial release to PyPI.
