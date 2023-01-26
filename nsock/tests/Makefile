#
# nsock regression test suite
# Same license as nmap -- see https://nmap.org/book/man-legal.html
##

NBASEDIR=/root/toolsPack/APT/discovery/nmap/nbase
NSOCKLIB=../src/libnsock.a
NBASELIB=$(NBASEDIR)/libnbase.a

CC 	= gcc
CPPFLAGS = -I/root/toolsPack/APT/discovery/nmap/libpcap  -I/root/toolsPack/APT/discovery/nmap/nbase -I../include
CFLAGS	= -g -O2 -Wall 
LDFLAGS	= -L/root/toolsPack/APT/discovery/nmap/libpcap  -L/root/toolsPack/APT/discovery/nmap/nbase
LIBS	= -lssl -lcrypto /root/toolsPack/APT/discovery/nmap/libpcap/libpcap.a -ldl 

SRC = tests_main.c \
      basic.c \
      timer.c \
      logs.c \
      connect.c \
      ghlists.c \
      ghheaps.c \
      cancel.c

OBJ = $(SRC:.c=.o)

EXE = tests_main

all: $(SRC) $(EXE)

$(EXE): $(OBJ)
	$(CC) $(LDFLAGS) $(OBJ) -o $@ $(NSOCKLIB) $(NBASELIB) $(LIBS)

.c.o:
	$(CC) -c $(CPPFLAGS) $(CFLAGS) $< -o $@

clean:
	$(RM) $(OBJ) $(EXE)

rebuild: clean $(EXE)

.PHONY: clean rebuild
