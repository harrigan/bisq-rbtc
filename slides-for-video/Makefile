LATEXMK = latexmk
CHKTEX = chktex
PREVIEW = open -a Preview
FSWATCH = fswatch
REFRESH = osascript -e 'tell application \"Preview\" to activate'

BASENAME = main
TEXFILES = $(BASENAME).tex
STYFILES =
IMGFILES =
BIBFILES =
MISCFILES =

INPUTFILES = $(TEXFILES) $(STYFILES) $(IMGFILES) $(BIBFILES) $(MISCFILES)
OUTPUTFILE = $(BASENAME).pdf

.PHONY: all check clean open watch

all: $(BASENAME).pdf

$(OUTPUTFILE): $(INPUTFILES)
	$(LATEXMK) -pdf -bibtex -use-make $<

check:
	$(CHKTEX) $(TEXFILES)

clean:
	$(LATEXMK) -pdf -bibtex -C

open: $(OUTPUTFILE)
	$(PREVIEW) $(OUTPUTFILE)

watch: open
	$(FSWATCH) -o $(INPUTFILES) | xargs -n1 sh -c "$(MAKE) all; $(REFRESH)"
