# Template for LaTeX Documents

This repository is a template for easily building and managing LaTeX documents using
[UseLATEX.cmake](https://gitlab.kitware.com/kmorel/UseLATEX/). It comes with a sample
document with minimal settings. For more options please refer to UseLATEX documentation.

**Implemented by:**

* [M.Mucahid Benlioglu](https://github.com/mbenlioglu)

## Building
#### Prerequisites:

- [CMake](https://cmake.org/) (> v3.14)
- [LaTeX](https://www.latex-project.org/get/)

To build the document, simply execute the following from the project root

	$ cd build/ && cmake .. && make

This will create compiled pdf file, `document.pdf`, in the `build` directory.

Alternatively, once you run `cmake` within `build` folder you can setup file watchers with 
a tool like `inotify-tools` to automatically build the pdf as soon as you save the files.
Here is an example script to run from the root of the project

```bash
inotifywait -m -e close_write . | while read -r directory events filename; do 
	if [[ "${filename##*.}" == tex || "${filename##*.}" == bib ]]; then
		cd build && make && cd ..
	fi
done
```
