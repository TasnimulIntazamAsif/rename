### Project overview

This project provides Jupyter notebooks to batch-rename images inside a folder. Each notebook targets a specific naming pattern and performs a safe two-step rename to avoid filename collisions while preserving original file extensions.

### Notebooks

- `renameCAP.ipynb`: Renames to `CAP_<PREFIX>_<index>` (e.g., `CAP_A_0`, `CAP_A_1`, …). The prefix is configurable (default shown in the notebook).
- `renameSMALL.ipynb`: Renames to `SMALL_<prefix>_<index>` (e.g., `SMALL_z_0`, `SMALL_z_1`, …). The prefix is configurable.
- `renameDIGIT.ipynb`: Renames to `DIGIT_<digitLabel>_<index>` (e.g., `DIGIT_0_1`, `DIGIT_0_2`, …). You choose the digit label and starting index.
- `renameFALL.ipynb`: Renames to `FALL-2024_<index>` (e.g., `FALL-2024_1`, `FALL-2024_2`, …). The semester prefix is configurable and index starts from 1. Works with all file types.

Across notebooks:
- You input a folder path.
- Images are detected by extension and sorted by filename before renaming.
- Original extensions are preserved.
- Renaming uses a temporary stage to prevent conflicts.

### Supported file types

- `.jpg`, `.jpeg`, `.png`, `.gif`, `.bmp`, `.tiff`, `.tif`, `.webp`, `.heic`, `.heif`

### Requirements

- Python 3.8+
- Jupyter Notebook or JupyterLab

Install Jupyter if needed:

```sh
pip install notebook  # or: pip install jupyterlab
```

### Usage

1. Launch Jupyter in this folder:
   ```sh
   jupyter notebook   # or: jupyter lab
   ```
2. Open the notebook you need:
   - `renameCAP.ipynb` for names like `CAP_A_0` …
   - `renameSMALL.ipynb` for names like `SMALL_z_0` …
   - `renameDIGIT.ipynb` for names like `DIGIT_0_1` …
   - `renameFALL.ipynb` for names like `FALL-2024_1` …
3. Run all cells. When prompted, paste the absolute folder path that contains the images, for example:
   - `D:\Dataset\capital\A`
   - `D:\Dataset\Small\z`
   - `D:\Dataset\Digits\0`
   - `D:\Dataset\Fall2024\Documents`
4. Provide the requested prefix/label and the starting index if prompted. The notebook prints a summary of renamed files.

### Naming patterns

- `renameCAP.ipynb`: `CAP_<Prefix>_<index>`
- `renameSMALL.ipynb`: `SMALL_<prefix>_<index>`
- `renameDIGIT.ipynb`: `DIGIT_<digitLabel>_<index>`
- `renameFALL.ipynb`: `FALL-2024_<index>` (or custom semester prefix) - works with all file types

The index range depends on the number of images and the start index. With 100 images and start index `0`, indices will be `0` … `99`.

### Collision safety

- Files are first moved to unique temporary names, then to final targets. If a final target already exists, the process stops to avoid overwriting.

### Tips and troubleshooting

- If you accidentally type JSON literals like `null`, `true`, or `false` unquoted in a cell, Python would normally raise `NameError`. The notebooks include a small helper cell to define these names so accidental usage does not break execution.
- To get exactly `DIGIT_0_1` … `DIGIT_0_99`, set the start index to `1` and ensure there are 99 images; with 100 images and start `1`, the last will be `DIGIT_0_100`.
- Ensure the folder path is correct and that you have write permissions.

### Version control

A `.gitignore` is included to ignore typical Python, Jupyter, environment, OS, and IDE artifacts.

### License

See `LICENSE` for details.
