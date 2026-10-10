# sEMG hand gesture recognition

Converts NinaPro DB1 MAT files into ten EMG channels with exercise/stimulus labels and compares KNN, decision tree, and random forest.

## Setup and execution

Use Python 3.11 and a separate virtual environment for this project. Run commands from this folder:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
python check_inputs.py
python -m jupyterlab
```

On Windows, activate with `.venv\Scripts\activate`. For notebooks, select this environment’s kernel and execute from the top in a fresh kernel. The first code cell exposes `INPUT_PATHS` where old machine-specific paths existed. `PROJECT_DATA_DIR` changes the base for those configured paths; remaining relative paths use the notebook working directory.

## Notebooks

- [sEMG_based_hand_gesture_detection.ipynb](sEMG_based_hand_gesture_detection.ipynb)

## Inputs

Supply these inputs yourself; no dataset is downloaded automatically:

- `sEMG_exercise_stimulus_DB1.csv`

## Outputs

A generated CSV, reports, and confusion matrices for exercise 1.

## Implementation and limitations

Alternatively generate the CSV from user-supplied DB1 .mat files with csv_generator.py. Requires emg (N×10), exercise (scalar or N samples), stimulus (N samples). Conversion retains the original CSV index layout. Train and test now share the training-fitted scaler. Random row splits of adjacent samples are not subject-independent evaluation.

To generate input: `python csv_generator.py /path/to/mat-files --output sEMG_exercise_stimulus_DB1.csv`.

## Verification

The workspace regression suite checks source/notebook validity and selected behavior with bundled or synthetic inputs. Full experiment training and historical metric reproduction are not implied. See the workspace `REFACTOR_REPORT.md` for exact test coverage and unresolved runtime requirements.

## Original authors

- [@mansibm6](https://www.github.com/mansibm6)

## Original references

These links were retained from the original project notes; availability and licensing must be checked by the person obtaining the data.

- https://www.github.com/mansibm6
- http://ninaweb.hevs.ch/node/3
- http://publications.hevs.ch/index.php/publications/show/1715
- http://www.nature.com/articles/sdata201453
- http://publications.hevs.ch/index.php/publications/show/1629
