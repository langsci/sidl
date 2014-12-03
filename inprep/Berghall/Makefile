# specify your main target here:
all: book pod cover

# specify thh main file and all the files that you are including
SOURCE= berghall.tex\
localbibliography.bib\
LSP/langsci.cls
	 
berghall.pdf: berghall.tex $(SOURCE)
	xelatex -no-pdf berghall 
	bibtex -min-crossrefs=200 berghall
	xelatex  -no-pdf berghall
	sed -i s/.*\\emph.*// berghall.adx #remove titles which biblatex puts into the name index
	makeindex -o berghall.and berghall.adx
	makeindex -o berghall.lnd berghall.ldx
	makeindex -o berghall.snd berghall.sdx
	xelatex -no-pdf berghall 
	xelatex berghall 

#create only the book
book: berghall.pdf 

#create a png of the cover
cover: berghall.pdf
	convert berghall.pdf\[0\] -resize 486x -background white -alpha remove -bordercolor black -border 2  cover.png
	display cover.png

#extract the front cover, back cover and spine from the pdf	
triptychon: berghall.pdf#output=long has to be used for this to work
	pdftk A=berghall.pdf cat  A1  output front.pdf 
	pdftk A=berghall.pdf cat A2 output back.pdf 
	pdftk A=berghall.pdf cat A3 output spine.pdf

#prepare for print on demand services	
pod: bod createspace

#prepare for submission to BOD
bod: triptychon #output=long has to be used for this to work
	pdftk A=berghall.pdf B=blank.pdf cat B A4-end output tmp.pdf 
	./filluppages tmp.pdf bod/bodcontent.pdf
	\rm tmp.pdf
	xelatex bodcover.tex
	mv bodcover.pdf bod/

# prepare for submission to createspace
createspace: triptychon #output=long has to be used for this to work
	xelatex createspacecover.tex
	mv createspacecover.pdf createspace
	pdftk A=berghall.pdf B=blank.pdf cat B A4-end output createspace/createspacecontent.pdf

#housekeeping	
clean:
	rm -f *.bak *~ *.backup *.tmp \
	*.adx *.and *.idx *.ind *.ldx *.lnd *.sdx *.snd *.rdx *.rnd *.wdx *.wnd \
	*.log *.blg *.ilg \
	*.aux *.toc *.cut *.out *.tpm *.bbl *-blx.bib \
	*.glg *.glo *.gls *.wrd *.wdv *.xdv 

realclean: clean
	rm -f *.dvi *.ps *.pdf 
