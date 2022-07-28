PROGNAME = repeater
SRC = repeater.c parseconfig.c json.c

OBJS = $(patsubst %.c,%.o,$(SRC))

CC = aarch64-linux-gnu-gcc -march=armv8-a
CFLAGS = -static -Wall -Werror -std=c99 -pedantic -I../include -D_POSIX_SOURCE -DDEBUG

build-release: $(OBJS)
	mkdir -p ../bin
	$(CC) $(CFLAGS) -o ../bin/$(PROGNAME) $(OBJS) -lm

build-debug: CFLAGS += -g -DDEBUG
build-debug: $(OBJS)
	mkdir -p ../bin
	$(CC) $(CFLAGS) -o ../bin/$(PROGNAME) $(OBJS) -lm

%.o: %.c ../include/%.h
	$(CC) $(CFLAGS) -c $< -lm

clean:
	rm -f ./*.o
	rm -rf ../bin
