# Customizing `bibtex` style
Daniel Bochen Tan
## Background
DOIs are good since they're constant while URLs are not.
DOI may not be supported in bibtex styles.
We want to modify the styles to append DOI to each bibliography item.
`bib` is the reference database, `bst` defines the bibliography style.
## Reverse Polish Notation
Input: 1 2 3 + x

Stack status: tb t1b t21b t321b t51b t5b
## Internal Operators
- `FUNCTION {NAME} {RETURN VALUE}`: definition of function.
- `STRING`: push to stack, e.g., `""`.
- All fields are read as strings, e.g., `doi`.
- `empty$`: check if the top is empty, push 1 if so, push 0 if not
- `{ACTION_1} {ACTION_0} if$`: check if the top is strictly larger than 0, do `ACTION_1` if so, do `ACTION_0` if not.

## Design `FUNCTION format.doi`
```
FUNCTION {format.doi}
{doi empty$
    { "" }
    { doi }
if$
}
```