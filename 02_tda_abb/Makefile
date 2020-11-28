EXEC= abb
OBJ= abb.o
CC= gcc
CFLAGS= -g -std=c99 -Wall -Wconversion -Wtype-limits -pedantic -Werror -O0 -o
VAL= valgrind
VFLAGS= --leak-check=full --track-origins=yes --show-reachable=yes
MINIPRUEBAS= abb.o abb_minipruebas.c
MASPRUEBAS:= abb.o abb_maspruebas.c
FILES= *.c *.h *.pdf Makefile README.md *.png
ENTREGA= tda_entrega.zip

lint:
	cppcheck --enable=all *.c

%.o: %.c %.h
	$(CC) $(CFLAGS) $@ -c $<

minipruebas: $(OBJ)
	$(CC) $(MINIPRUEBAS) $(CFLAGS) $(EXEC)
	$(VAL) $(VFLAGS) ./$(EXEC)

minipruebas_v: $(OBJ)
	$(CC) $(MINIPRUEBAS) $(CFLAGS) $(EXEC)
	$(VAL) $(VFLAGS) -v ./$(EXEC)

maspruebas: $(OBJ)
	$(CC) $(MASPRUEBAS) $(CFLAGS) $(EXEC)
	$(VAL) $(VFLAGS) ./$(EXEC)

maspruebas_v: $(OBJ)
	$(CC) $(MASPRUEBAS) $(CFLAGS) $(EXEC)
	$(VAL) $(VFLAGS) -v ./$(EXEC)

debug: $(EXEC)
	gdb --tui ./$(EXEC)

clean:
	rm $(EXEC) $(OBJ) $(ENTREGA)

entrega:
	zip $(ENTREGA) $(FILES)
