# UnvibeCode re-export reproduction

UnvibeCode 0.3.15 reports ambiguous_symbol for a name that pkg/__init__.py explicitly re-exports.

Files: pkg/__init__.py (from .funcs import Thing as Thing), pkg/funcs.py (def Thing), pkg/classes.py (class Thing), app.py (from pkg import Thing).

Reproduce: python -m unvibecode review --repository PATH_TO_THIS_FOLDER --no-open-browser, then open unresolved_relationships.jsonl inside the generated repository-context ZIP.

Expected: app.py links to pkg/funcs.py. Actual: ambiguous_symbol and no symbol edge.

Control: delete pkg/classes.py and run again; the link to pkg/funcs.py appears.
