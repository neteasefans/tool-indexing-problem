# Short- and long-term memory coordinated tabu search for the tool indexing problem

This repository contains the source code, benchmark instances, and best solutions for the short- and long-term memory coordinated tabu search (SLTS) algorithm for the tool indexing problem (TIP) without tool duplication.

The benchmark testbed comprises 85 instances from five sets: Anjos, Sko, O, S, and Y. It includes 52 small instances and 33 large instances. These instance sets have been used in previous TIP studies, including Atta et al. (2019), referenced below. To facilitate further research, the benchmark files are provided in the `instances` directory.

## How to run the program

The program is written in C. Compilation requires GCC with C11 support and GNU make. The supplied makefile uses the `-O2` optimization option.

### To compile

Place `SLTS_parallel5.c` and `makefile` in the repository root, then run:

```sh
make
```

On Windows with MinGW make, use `mingw32-make` instead. The generated executable is named `SLTS5.exe`.

### To run

```sh
./SLTS5.exe input_file seed slot_count
```

The three arguments are:

- `input_file`: the path to the instance file containing the tool transition frequency matrix.
- `seed`: the random seed, such as `0`, `1`, or `2`.
- `slot_count`: the total number of slots in the tool magazine, denoted by `n` in the paper. This value must be at least the number of tools, which is obtained from the input matrix.

Each run writes the best cost, runtime information, and best tool positions to standard output. In the `best_u` output, the k-th value gives the slot occupied by tool k, with indices starting at 1. To save the output, append `> output_file.txt` to the run command.

To display the program settings, run:

```sh
./SLTS5.exe --info
```

## Materials

This repository includes the following materials:

- `instances/`: benchmark instance files used in the experiments.
- `solutions/`: best solutions found by SLTS for the benchmark instances.
- `SLTS_parallel5.c`: C source code of SLTS.
- `makefile`: compilation instructions for the source code.
- `build_SLTS.ps1`: Windows compilation script.
- `run_all_SLTS.ps1`: Windows batch-experiment script.

The PowerShell scripts require PowerShell 7 or later.

## Reference

Atta, S., Sinha Mahapatra, P. R., and Mukhopadhyay, A. (2019). Solving tool indexing problem using harmony search algorithm with harmony refinement. *Soft Computing*, 23, 7407-7423. https://doi.org/10.1007/s00500-018-3385-5
