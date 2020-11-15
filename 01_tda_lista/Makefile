EXEC= lista_se
OBJ= lista.o
CC= gcc
CFLAGS= -g -std=c99 -Wall -Wconversion -Wtype-limits -pedantic -Werror -O0 -o
VAL= valgrind
VFLAGS= --leak-check=full --track-origins=yes --show-reachable=yes
MINIPRUEBAS= lista.o lista_minipruebas.c
MASPRUEBAS:= lista.o lista_maspruebas.c
FILES= *.c *.h *.pdf Makefile README.md *.png
ENTREGA= tda_entrega.zip

lint:
	cppcheck --enable=all *.c

%.o: %.c %.h
	$(CC) $(CFLAGS) $@ -c $<

minipruebas: lista.o
	$(CC) $(MINIPRUEBAS) $(CFLAGS) $(EXEC)
	$(VAL) $(VFLAGS) -v ./$(EXEC)

maspruebas: lista.o
	$(CC) $(MASPRUEBAS) $(CFLAGS) $(EXEC)
	$(VAL) $(VFLAGS) ./$(EXEC)

maspruebas_v: lista.o
	$(CC) $(MASPRUEBAS) $(CFLAGS) $(EXEC)
	$(VAL) $(VFLAGS) -v ./$(EXEC) mostrar_pruebas

debug: $(EXEC)
	gdb --tui ./$(EXEC)

clean:
	rm $(EXEC) $(OBJ) $(ENTREGA)

entrega:
	zip $(ENTREGA) $(FILES)
