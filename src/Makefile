IDIR = ./include
CC=gcc
CFLAGS=-I$(IDIR) # -g -O0

ODIR=obj
LDIR =-L./lib -L/lib64
LIBS=`pkg-config --cflags --libs jansson` `pkg-config --cflags --libs libconfig`
#LDFLAGS=-shared

_DEPS = client.h file.h file_system.h main.h parse_file.h protocol.h server.h session.h sessions.h signals.h tasks.h
DEPS = $(patsubst %,$(IDIR)/%,$(_DEPS))

_OBJ = client.o file_system.o main.o parse_file.o protocol.o server.o sessions.o signals.o tasks.o
OBJ = $(patsubst %,$(ODIR)/%,$(_OBJ))


$(ODIR)/%.o: %.c $(DEPS)
	$(CC) -c -o $@ $< $(CFLAGS)

all: sync_p2p

sync_p2p: $(OBJ)
	$(CC) -o $@ $^ $(CFLAGS) $(LDFLAGS) $(LDIR) $(LIBS)

#.PHONY: clean

clean:
	rm -f sync_p2p core $(ODIR)/*.o *~ $(IDIR)/*~ 
