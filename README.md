# Conway's Game of Life (C)

Console implementation of [Conway's Game of Life](https://en.wikipedia.org/wiki/Conway%27s_Game_of_Life) written in C as the final project (Tugas Besar, Modul 9) of EL2208 *Praktikum Pemecahan Masalah dengan C* 2019/2020, Kelompok 5:

- Cedric Samuel (13218060)
- Muhammad Ali Novandhika (13218067)
- Achmad Rifqy Pratama (13218069)
- Muhammad Heronan Hyanda (13218073)

The program reads an initial pattern (seed) from a text file and evolves it on a **toroidal** grid (edges wrap around) using the standard rules: a live cell with fewer than 2 or more than 3 live neighbours dies, a live cell with 2 or 3 survives, and a dead cell with exactly 3 becomes alive.

## Files

| Path | Description |
| --- | --- |
| `utamaTUBESFINAL.c` | Final program (`main`, menu and file handling). |
| `gameFuncFINAL.h` | Game logic used by the final program (grid I/O, neighbour count, next generation, animation). |
| `SeedFile_<NIM>.txt` | Seed patterns made by each group member. |
| `gameoflifefile.txt` | Gosper glider gun seed. |
| `archive/` | Earlier revisions and experiments kept for reference (not needed to build). |

## Build

```bash
gcc utamaTUBESFINAL.c -o gameoflife
```

`gameFuncFINAL.h` contains function definitions and is included directly by `utamaTUBESFINAL.c`, so only the `.c` file is compiled.

The program uses `system("cls")` to clear the screen and `gets()` for input, so it targets Windows (e.g. MinGW gcc). On Linux/macOS the screen will not clear, and newer compilers/C standards may warn about or reject `gets()`.

## Run

```bash
./gameoflife        # Windows: gameoflife.exe
```

1. Enter the seed file name, e.g. `SeedFile_13218069.txt` (path is relative to the current directory; you are asked again if the file is not found).
2. The seed is printed, then choose from the menu:
   - `1` **Animate** – run a given number of iterations.
   - `2` **Tick** – advance one generation.
   - `3` **End of Generation** – keep iterating until the grid stops changing (a pattern that never stabilises will loop forever).
   - `4` **Quit** – asks whether to continue: `Y` loads a new seed file, `N` exits.

## Seed file format

```
<rows>
<columns>
<row 1: exactly <columns> characters of X or ->
...
<row N>
# free-text comment / description of the pattern
```

- `X` is a live cell, `-` is a dead cell.
- Reading stops at the first `#`, so the description goes after the grid.
- The seed files in this repo use Windows (CRLF) line endings, which matches the intended Windows build.

Example (`SeedFile_13218073.txt` begins with):

```
15
20
--------------------
--------------------
--------------------
--------------------
-------XXXXXXX------
...
```
