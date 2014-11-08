.SUFFIXES: .tex .gp .eps .pdf
LC = pdflatex
FLAGS = -shell-escape
PLOTS = examplefig
PLOTINCLUDES = $(PLOTS:=.tex)
GNUPLOTSCRIPTS = $(PLOTS:=.gp)
EPSS = $(PLOTS:=.eps)

rap: rap.tex $(PLOTINCLUDES) frontpage.pdf
	$(LC) $(FLAGS) rap.tex

# Always make eps and tex when gnuplotting through Make
%.tex: %.gp
	gnuplot -e $(subst filename,$@,"set terminal epslatex color solid; set output 'filename'") $<

frontpage.pdf: frontpage.tex
	$(LC) $(FLAGS) frontpage.tex

.PHONY: clean veryclean show

show:
	mupdf rap.pdf

clean:
	rm -vf $(EPSS) $(PLOTINCLUDES) *.aux *.toc *.log framsida.pdf $(PLOTS:=-eps-converted-to.pdf)

veryclean:
	rm -vf $(EPSS) $(PLOTINCLUDES) *.aux *.toc *.log framsida.pdf $(PLOTS:=-eps-converted-to.pdf) rap.pdf frontpage.pdf
