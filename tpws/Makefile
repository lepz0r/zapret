CC ?= gcc
CFLAGS += -std=gnu99 -Wno-logical-op-parentheses -O3
CFLAGS_BSD = -Wno-address-of-packed-member -Wno-switch
CFLAGS_MAC = -mmacosx-version-min=10.8
LIBS = -lz
SRC_FILES = *.c

all: tpws

tpws: $(SRC_FILES)
	$(CC) -s $(CFLAGS) -o $@ $(SRC_FILES) $(LDFLAGS) $(LIBS)

bsd: $(SRC_FILES)
	$(CC) -s $(CFLAGS) $(CFLAGS_BSD) -Iepoll-shim/include -o tpws $(SRC_FILES) epoll-shim/src/*.c $(LDFLAGS) $(LIBS)

mac: $(SRC_FILES)
	$(CC) $(CFLAGS) $(CFLAGS_BSD) $(CFLAGS_MAC) -Iepoll-shim/include -Imacos -o tpws $(SRC_FILES) epoll-shim/src/*.c $(LDFLAGS) $(LIBS)
	strip tpws

clean:
	rm -f tpws *.o
