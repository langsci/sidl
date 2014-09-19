# specify your main target here:
all: riessler.pdf

# specify the main file and all the files that you are including
SOURCE= riessler.tex chapters/abbreviations.tex chapters/appendix.tex chapters/chap-areal.tex chapters/chap-areal-typ.tex chapters/chap-evolution-nea.tex chapters/chap-interface.tex chapters/chap-intro.tex chapters/chap-lg-nea.tex chapters/chap-np-adj.tex chapters/chap-ontology.tex chapters/chap-polyfunctionality.tex chapters/chap-results.tex chapters/chap-syn-introduction.tex chapters/chap-typologizing-np.tex chapters/chap-typology-of.tex chapters/part-concl.tex chapters/part-diachrony.tex chapters/part-synchrony.tex chapters/part-theory.tex chapters/part-typology.tex chapters/preface.tex\
LSP/langsci.cls
	 
riessler.pdf: riessler.tex  $(SOURCE)
	xelatex -no-pdf riessler.tex 
#	bibtex -min-crossrefs=200 $*
	xelatex -no-pdf riessler.tex 
#	bibtex -min-crossrefs=200 $*
#	xelatex  -no-pdf $*
	makeindex -o riessler.ind riessler.idx
	makeindex -o riessler.lnd riessler.ldx
#	makeindex -o $*.wnd $*.wdx
#	LSP/bin/reverse-index <$*.wdx >$*.rdx
#	makeindex -o $*.rnd $*.rdx
	\rm riessler.adx	
#	authorindex -i -p riessler.aux > riessler.adx
#	sed -e 's/}{/|hyperpage}{/g' riessler.adx > riessler.adx.hyp
#	makeindex -o riessler.and riessler.adx.hyp
	xelatex -no-pdf riessler.tex 
	xelatex riessler.tex 


# http://stackoverflow.com/questions/10934456/imagemagick-pdf-to-jpgs-sometimes-results-in-black-background
cover: XeTeX_piteSaami_SDL.pdf
	convert $*.pdf\[0\] -resize 486x -background white -alpha remove -bordercolor black -border 2  cover.png

# convert $*.pdf\[0\] -resize 486x -background white -alpha remove -bordercolor black -border 2  cover.png

# 204x303 with a 2x2 margin it has to be 200x299
#convert tmp.pdf\[0\] -resize x299 -background white -alpha remove -bordercolor black -border 2  -quality 100 cover.png

# does not seem to have any effect:
# http://www.imagemagick.org/script/command-line-options.php#quality

clean:
	rm -f *.bak *~ *.log *.blg *.aux *.toc *.cut *.out *.tmp *.tpm *.adx *.adx.hyp *.idx *.ilg \
	*.and *.glg *.glo *.gls *.wdx *.wnd *.wrd *.wdv *.ldx *.lnd *.rdx *.rnd *.xdv 

realclean: clean
	rm -f *.dvi *.ps *.pdf *.bbl

