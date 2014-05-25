IDIR = ./include
CC=gcc
CFLAGS=-I$(IDIR) -fPIC

ODIR=obj
LDIR =-L./lib -L/lib64
LIBS=-lm -ljson
LDFLAGS=-shared

_DEPS = client.h file.h file_system.h main.h parse_file.h protocol.h server.h session.h sessions.h signals.h tasks.h
DEPS = $(patsubst %,$(IDIR)/%,$(_DEPS))

_OBJ = client.o file_system.o main.o parse_file.o protocol.o server.o sessions.o signals.o tasks.o
OBJ = $(patsubst %,$(ODIR)/%,$(_OBJ))


$(ODIR)/%.o: %.c $(DEPS)
	$(CC) -c -o $@ $< $(CFLAGS)

sync_p2p: $(OBJ)
	gcc -o $@ $^ $(CFLAGS) $(LDFLAGS) $(LDIR) $(LIBS)

#.PHONY: clean

clean:
	rm -f sync_p2p core $(ODIR)/*.o *~ $(IDIR)/*~ 
