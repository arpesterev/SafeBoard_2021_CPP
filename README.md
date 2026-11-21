# SafeBoard 2021: C++ task

A C++17 command-line utility written for the second stage of the Kaspersky SafeBoard 2021 selection. It inspects files in a supplied directory and identifies certain signatures associated with Unix, macOS and JavaScript files.

The source also contains a Linux daemon variant and a script for generating test inputs.

## Build

The Makefile expects the `build/` directory to exist:

```sh
mkdir -p build
make linux_target
```

On macOS, use `make macOS_target` instead. Both targets build `build/scan_util` with `g++` and C++17 flags.

## Run

```sh
./build/scan_util /path/to/directory
```

The program scans regular files directly inside the supplied directory and prints counts. It is a signature-based experiment, not a malware detector or a substitute for antivirus software.

## Code map

- [`main.cpp`](main.cpp): argument handling, directory iteration and signature checks.
- [`Makefile`](Makefile): build variants.
- [`generate_tests.py`](generate_tests.py): generation of test inputs.
- [`utility/`](utility/): supporting utility source.

## Testing caveat

The checked-in `make tests` target relies on a `TARGET` variable that is not set in the Makefile. It may need manual adjustment before it runs. This README documents the source as it exists and does not claim that tests pass.
