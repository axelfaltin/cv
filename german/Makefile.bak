# ##########################################################################
# Einfaches Makefile zum Uebersetzen der Programme aus der ersten Aufgabe.
# ##########################################################################

# Variablendefinitionen (so aehnlich wie im Shell-Skript):
#

ALL=cv.de.tex cv.de.ps cv.de.pdf cv.de

# Der Name des Compilers:
PROG1=latex
PROG2=dvips
PROG3=latex2html
PROG4=makeindex
PROG5=ps2pdf14
PROG6=delatex 
PROG7=tar
PROG8=pstops 
PROG9=pdflatex


# Optionen zum Compiler (Debug-Code erzeugen): 
PROG1FLAGS=--src
PROG2FLAGS= -Ppdf
PROG3FLAGS= -address me@axel-faltin.de 
PROG4FLAGS=
PROG5FLAGS=
PROG6FLAGS=
PROG7FLAGS= -cvzf cw.tgz
PROG8FLAGS="2:0L@.7(21cm,0)+1L@.7(21cm,14.85cm)"
PROG9FLAGS=

.PHONY= all, html, wc

 
# Das Standard-Target (das Programm "prog"):
all: dvi 

#
# Weitere Sub-Targets, Regeln und Abhaengigkeiten:
#

# Die Abhaengigkeiten von .c zu .o Dateien. Wie aus .c Dateien die
# dazugehoerigen .o Dateien erzeugt werden, steht weiter unten.

cv.de.dvi: cv.de.tex

# Hier haben wir die Abhaengigkeit der zu erzeugenden Programme von den
# dazugehoerigen Objektdateien und eine spezielle Regel zum Erzeugen
# der ausfuehrbaren Datei "prog" aus den Objektdateien. Wichtig ist, 
# dass in der zweiten Zeile das erste Zeichen ein "Tab" sein muss!

dvi: 
	$(PROG1) $(PROG1FLAGS) cv.de.tex 

ps: dvi
	$(PROG2) $(PROG2FLAGS) cv.de.dvi

html:
	$(PROG3) $(PROG3FLAGS) cv.de.tex

index: dvi
	$(PROG4) $(PROG4FLAGS) cv.de.idx

pdf: ps
	$(PROG5) $(PROG5FLAGS) cv.de.ps

wc: 
	$(PROG6) $(PROG6FLAGS) cv.de.tex | wc -w

zip: pdf	
	$(PROG7) $(PROG7FLAGS) $(ALL)

cv2: ps
	$(PROG8) $(PROG8FLAGS) cv.de.ps cv2.de.ps 

pdfl:
	$(PROG9) $(PROG9FLAGS) cv.de.tex



# Eine allgemeine Regel, wie aus einer .c Datei eine .o Datei erzeugt wird.
# In der ersten Zeile steht, worum es geht, in der zweiten Zeile steht,
# wie es gemacht wird. Wichtig: die zweite Zeile muss mit einem <TAB> Zeichen
# beginnen! Alle Sachen, die mit einem "$" anfangen, sind Variablen. Die
# Variablen mit Namen in runden Klammern sind die oben definierten. Die 
# anderen sind Systemvariablen: $< ist der Dateiname auf den der Ausdruck
# rechts vom ":" in der ersten Zeile passt, $@ ist der entsprechende fuer
# den Ausdruck rechts vom ":".

%.dvi: %.tex
	$(PROG1) $(PROG1FLAGS) $<

%.ps: %.dvi
	$(PROG2) $(PROG2FLAGS) $<

%.pdf: %.ps
	$(PROG5) $(PROG5FLAGS) $<


# Ueblicherweise definiert man ein Target "clean", durch das ggf. alle
# erzeugten Dateien geloescht werden, damit man sie wieder neu compilieren
# kann:

clean: 
	-rm -r cv.de.dvi cv.de.lot cv.de.log cv.de.aux cv.de.lof cv.de.toc cv.de.ps cv.de.idx cv.de.ilg cv.de.ind cv.de.pdf cv.de cv2.de.ps 
