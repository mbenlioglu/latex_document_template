cmake_minimum_required(VERSION 3.14)

# Add UseLATEX v2.7.2
include(FetchContent)
FetchContent_Declare(
    UseLATEX
    GIT_REPOSITORY  https://gitlab.kitware.com/kmorel/UseLATEX.git
    GIT_TAG         Version2.7.2
)
FetchContent_MakeAvailable(UseLATEX)
include(${uselatex_SOURCE_DIR}/UseLATEX.cmake)

project("LaTeX Document Template" NONE)

set(PDFLATEX_COMPILER pdflatex)

# Output documents
add_latex_document(document.tex
    BIBFILES    references.bib
    INPUTS      functions.tex
)

