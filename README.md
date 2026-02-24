# Apache Arrow Courses

A hands-on notebook series covering Apache Arrow from first principles to the low-level C Data Interface.

## Setup

Requires [pixi](https://pixi.sh) (conda-forge package manager).

```bash
# Install all dependencies (including xeus-python kernel)
pixi install

# Launch JupyterLab
pixi run lab
```

> JupyterLab opens at `http://localhost:8888` with the `notebooks/` folder.  
> All notebooks use the **xeus-python** kernel (`xpython`).

## Pre-commit (strip notebook outputs)

To ensure notebook outputs are cleared before each commit:

```bash
# Install dependencies (if not already done)
pixi install

# Install git pre-commit hooks
pixi run precommit-install
```

To clean existing notebooks and verify all hooks:

```bash
pixi run precommit-run
```

## Course Outline

| # | Notebook | Level | Topics |
|---|----------|-------|--------|
| 01 | `01_why_arrow.ipynb` | Beginner | Why columnar? Row vs columnar benchmark, Arrow guarantees, vocabulary (Array, Buffer, Schema, RecordBatch, Table) |
| 02 | `02_arrays_buffers_nulls.ipynb` | Beginner | Fixed-size primitive layout, buffer inspection, validity bitmaps, LSB bit decoding, null optimizations |
| 03 | `03_variable_length_and_nested.ipynb` | Intermediate | VarBinary offset buffers, Utf8View inline/pointer, List/FixedSizeList, Struct AND-bitmap, Dense/Sparse Union |
| 04 | `04_dictionary_and_ree.ipynb` | Intermediate | Dictionary encoding memory savings, Run-End Encoding, O(log n) random access with binary search |
| 05 | `05_ipc_streaming_file.ipynb` | Intermediate | IPC wire format bytes, continuation marker, EOS, streaming vs file, ARROW1 magic, random access, lz4/zstd |
| 06 | `06_extension_types.ipynb` | Advanced | Custom Extension types, parameterized metadata, IPC round-trip, `ARROW:extension:name` |
| 07 | `07_c_data_interface_pycapsule.ipynb` | Advanced | C Data Interface goals, ArrowSchema/ArrowArray structs, PyCapsule protocol (`__arrow_c_array__`), zero-copy verification, stream interface |
| 08 | `08_c_data_interface_ctypes.ipynb` | Expert | ctypes struct definitions, `malloc`-based producer, release callbacks, move semantics, `struct<float32,utf8>` producer, metadata binary format |

## Source Material

- [Apache Arrow Columnar Format](https://arrow.apache.org/docs/format/Columnar.html)
- [C Data Interface Specification](https://arrow.apache.org/docs/format/CDataInterface.html)
- [PyCapsule Interface](https://arrow.apache.org/docs/format/CDataInterface/PyCapsuleInterface.html)
