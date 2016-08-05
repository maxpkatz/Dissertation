EPStoPDF = epstopdf

ALL: dissertation.ps dissertation.pdf 

eps_source = $(wildcard plots/*.eps)

pdf_source = $(eps_source:.eps=.pdf)

dissertation.dvi: dissertation.tex refs.bib $(eps_source)
	latex dissertation.tex < /dev/null
	bibtex dissertation < /dev/null
	latex dissertation.tex < /dev/null
	latex dissertation.tex < /dev/null
	latex dissertation.tex < /dev/null

dissertation.pdf: dissertation.tex refs.bib $(pdf_source)
	pdflatex dissertation.tex < /dev/null
	bibtex dissertation < /dev/null
	pdflatex dissertation.tex < /dev/null
	pdflatex dissertation.tex < /dev/null
	pdflatex dissertation.tex < /dev/null

pdf:	dissertation.pdf 

%.ps: %.dvi
	dvips -t letter -o $@ $<

%.pdf: %.eps
	$(EPStoPDF) $<

clean:
	$(RM) $(pdf_source) *.dvi 
	$(RM) *.blg *.log *.brf
	$(RM) *.lof *.lot
	$(RM) *.aux *.ps *.bbl
	$(RM) *.pdf *.out
	$(RM) *.toc
	$(RM) *~
	$(RM) plots/*.aux
	$(RM) plots/*.pdf
	$(RM) plots/*~

.PHONY: clean
