LATEXMK=latexmk
LATEXMK_ARGS=-xelatex -interaction=nonstopmode -halt-on-error -outdir=build

.PHONY: build clean
build:
	$(LATEXMK) $(LATEXMK_ARGS) main.tex
	cp build/main.pdf main.pdf

clean:
	$(LATEXMK) -outdir=build -c main.tex
