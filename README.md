# Minimal Nim kernel for Jupyter

This is a rough adaptation of https://github.com/brendan-rius/jupyter-c-kernel .
It's mostly functional, there are probably bugs lurking around.

Look at [example-notebook](https://github.com/stisa/jupyter-nim-kernel/blob/master/example-notebook.ipynb) for some examples.

**NOTE**: Context is **NOT** shared between blocks!!
I'll try working on it when I have time.

## Magics
Currently implemented magics are:

- `#>loadblock <num>` : load block `num` in the current block, automatically disables `echo` calls in loaded block.  
Partial workaround for sharing context.
- `#>passflag <someflag>` : pass a flag to the compiler, eg `--verbosity:3`, `--d:openblas` etc.  
**Currently one flag per line**  

## Prereqs
- a working `nim` installation ( [download](http://nim-lang.org/download.html) )
- a working `jupyter` (and  **python 3^**) installation ( I recomend [miniconda3](http://conda.pydata.org/miniconda.html) and adding jupyter with `conda install jupyter` )

## Installation
- `pip install jupyter_nim_kernel`
- `git clone https://github.com/stisa/jupyter-nim-kernel.git`
- `cd jupyter-nim-kernel`
- `jupyter-kernelspec install nim_spec/`
- Done, now run `jupyter-notebook` and select `new->Nim`

## Manual Installation
- `git clone https://github.com/stisa/jupyter-nim-kernel.git`
- `cd jupyter-nim-kernel`
- `pip install -e .`
- `jupyter-kernelspec install nim_spec/`
- Done, now run `jupyter-notebook` and select `new->Nim`

## Note
Forked from https://github.com/brendan-rius/jupyter-c-kernel and adapted to work 
with [nim](nim-lang.org).  

This a simple proof of concept. It's not intended to be used in production in its current shape.   

## Known bugs
- The output is littered with `Hint: [Processing]...` statements
- Every block is treated as a separate file ( not really a bug, it's just not yet implemented )
- Others?

## License
[MIT](LICENSE.txt)

## TODO
- have a look at implementing [nimsuggest](https://github.com/nim-lang/nimsuggest)
- share context between blocks ( or at least procs, maybe an internal file that adds all procs and then is included before compilation? )
- ~~snippets~~
- ~~basic completion~~