# P300 Analyzer
> *Note*: As of 2020-10-26, the speller has been moved to its own
[repository](https://github.com/bstadlbauer/lsl-p300-speller) and this repository has been renamed from `p300` to
`lsl-p300-analyzer`.

A tool for teaching P300 by showing the ongoing averaging process and continuous classification. The main purpose
of this tool is to visually show how the averaging in in a P300 paradigm works.

## Structure
Connections between the components is made using [LSL](https://github.com/sccn/labstreaminglayer).

Technically, this package supports all EEG recorders capable of streaming to LSL, however, at the moment
it is optimized to work with [eego sports](https://www.ant-neuro.com/products/eego_sports) by ANT neuro. If the
amplifier is changed, one wants to make sure the correct reference is chosen. As the ANT neuro has an internal
reference subtraction this is not necessary, but can easily be activated for other amplifiers changing the two
indicated lines in `bstadlbauer.p300.analyzer.data.RecordedData` (lines are commented at the moment).

In addition to this project a [speller](https://github.com/bstadlbauer/lsl-p300-speller), which provides the required
format via LSL. However, any speller using LSL should work.

## Installation

### Dependencies
This project uses [poetry](https://python-poetry.org/) to manage its dependencies. Visit their website on how to install
poetry for you operating system. The whole projects supports `python>=3.6.1`.

### Installing the package
Run the following to install the `bstadlbauer.p300speller` package:
```
git clone https://github.org/bstadlbauer/lsl-p300-speller
poetry install
```
which will setup a new virtual environment for the project and install the necessary dependencies.

## Getting Started
This project provides an entrypoint to start the analyzer, to do so - run the following after installation:
```
poetry run start-analyzer
```
One needs to know the number of the electrode (in the LSL stream) that
should be observed. Watch out, indexing for the electrodes starts at 0.

## Questions and Issues
If there are any questions or you run into an issue, please file a 'Issue' at the top.

## Contributing
If you want to contribute, please file also file an issue first where the new feature can be discussed, in general
contribution is welcome!

To setup the development environment, do the following:
```
git clone https://github.org/bstadlbauer/p300
poetry install
pre-commit install
```
To ensure consistent formatting and linting pre-commit hooks (managed through [`pre-commit`](https://pre-commit.com/))
are used.

### Testserver
For convenience, a testserver is available in the `testserver` package. It uses open-access data from BNCI Horizon,
upon first start the test data will be downloaded to `$XDG_CACHE_DIR/bstadlbauer/p300/testserver/003-2015`. To
start the server simply run the following:
```
poetry shell
python start_testserver.py
```
Watch out - even though the testserver produces a valid EEG stream, the averaging will not correctly work for it. So
the test-server can only be used to test the general data structure, but not to validate the algorithms.

# Acknowledgement
This tool was developed by myself as part of a project done at the
[Institute of Neural Engineering](https://www.tugraz.at/institutes/ine/home/).
The work was supervised by Assoc.Prof. Dipl.-Ing. Dr.techn. Reinhold Scherer.
