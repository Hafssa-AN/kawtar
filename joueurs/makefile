all: dep install

# Pour activer le mode debugage, il faut définir __DEBUG__
debug: DEBUG=-D'__DEBUG__'
debug: dep install

dep:
	cd ../libavalam; make
	cd ../libjoueur; make

LIB=-L../tournoi/lib
INC=-I../include
OPTS=-D_POSIX_C_SOURCE=199309L -std=c99


SRC=humain1.c humain2.c humain3.c joueur1.c joueur2.c joueur3.c joueur4.c joueur5.c

EXE=$(SRC:.c=.exe)
STATIC=$(SRC:.c=.static)

exe: $(EXE)
static: $(STATIC)

install: dep exe
	cp $(EXE) ../tournoi/bin

%.exe : %.c
	gcc $(OPTS) $(DEBUG) $(LIB) $(INC) $< -o $@ -lm -ljoueur -lpthread -lavalam

%.static : %.c
	gcc $(DEBUG) -static $(LIB) $(INC) $< -o $@ -lm -ljoueur -lpthread -lavalam

clean: 
	rm -rf $(EXE) $(STATIC)
	cd ../tournoi/bin; rm -rf $(EXE) $(STATIC)

cleanall: clean
	cd ../libavalam; make clean
	cd ../libjoueur; make clean


