# ##########################################################################
# Einfaches Makefile zum Uebersetzen der Programme aus der ersten Aufgabe.
# ##########################################################################

# Variablendefinitionen (so aehnlich wie im Shell-Skript):
#

ALL=cv.us.tex cv.us.ps cv.us.pdf cv.us

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
PROG3FLAGS= -address mail@axel-faltin.de 
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

cv.us.dvi: cv.us.tex

# Hier haben wir die Abhaengigkeit der zu erzeugenden Programme von den
# dazugehoerigen Objektdateien und eine spezielle Regel zum Erzeugen
# der ausfuehrbaren Datei "prog" aus den Objektdateien. Wichtig ist, 
# dass in der zweiten Zeile das erste Zeichen ein "Tab" sein muss!

dvi: 
	$(PROG1) $(PROG1FLAGS) cv.us.tex 

ps: dvi
	$(PROG2) $(PROG2FLAGS) cv.us.dvi

html:
	$(PROG3) $(PROG3FLAGS) cv.us.tex

index: dvi
	$(PROG4) $(PROG4FLAGS) cv.us.idx

pdf: ps
	$(PROG5) $(PROG5FLAGS) cv.us.ps

wc: 
	$(PROG6) $(PROG6FLAGS) cv.us.tex | wc -w

zip: pdf	
	$(PROG7) $(PROG7FLAGS) $(ALL)

cv2: ps
	$(PROG8) $(PROG8FLAGS) cv.us.ps cv2.us.ps 

pdfl:
	$(PROG9) $(PROG9FLAGS) cv.us.tex



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
	-rm -r cv.us.dvi cv.us.lot cv.us.log cv.us.aux cv.us.lof cv.us.toc cv.us.ps cv.us.idx cv.us.ilg cv.us.ind cv.us.pdf cv.us cv2.us.ps 
