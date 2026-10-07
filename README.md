SUPPLEMENTARY MATERIAL
SDo-Transformer: Causal Structure-Based Observational and Soft-Interventional Forecasting for Industrial Processes

DESCRIPTION
This package contains complete 22-by-22 SGP adjacency matrices for lags
1 through 5, a variable dictionary, and the settings used to generate the
matrices. Readers can inspect the weights or load them for numerical analysis.

CONTENTS
Supplementary Material.docx: matrix documentation and Tables S1--S5.
sgp_adjacency_lag_01.csv through sgp_adjacency_lag_05.csv: five lag matrices.
sgp_variables.xlsx: 22 node definitions and their physical/control units.
structure_run_config.json: model, training, and graph-export settings.
README.txt: this file.

DATA CONVENTIONS
CSV files use UTF-8 encoding, commas, and a header row. Each matrix file
has 22 data rows, one row-identifier column, and 22 numerical columns.
Rows are receiving nodes; columns are source nodes. Entry [j, i] represents
i -> j. Both axes follow M1--M8, X1--X14. Values are dimensionless and
rounded to four decimal places. Each matrix includes all 484 entries.
Lag k corresponds to k sampling steps, with a sampling interval of 2 s.
The variable dictionary fields are variable, type, description, unit, and
forecast_target. The target flag is 1 for X1, X2, and X5, and 0 otherwise.


PLATFORM AND ENVIRONMENT
The DOCX can be read with Microsoft Word or a compatible word processor.
CSV, TXT, XLSX and JSON files can be read on Windows, macOS, or Linux.
The optional loading example below requires Python 3.10 or later and uses
only the standard library. No network connection or model runtime is needed.

SETUP AND RUN
1. Extract all files into one directory.
2. Open Supplementary Material.docx to inspect the matrix tables, or open
   the CSV files with UTF-8 encoding and comma as the delimiter.
3. To load a matrix in Python, run the following from that directory:

   import csv
   with open('sgp_adjacency_lag_01.csv', encoding='utf-8', newline='') as f:
       rows = list(csv.reader(f))
   sources = rows[0][1:]
   targets = [row[0] for row in rows[1:]]
   weights = [[float(v) for v in row[1:]] for row in rows[1:]]
   print(len(targets), len(sources))
