
CC  = gcc
CXX = g++

INCLUDE = -I  /usr/local/include/safeheron  \
-I /usr/local/include

CFLAGS = -O2 -g -Wall
CXXFLAGS = -O2 -g -Wall -std=c++11 -arch arm64




OBJ  = main person wrapper
OBJS = $(addsuffix .o,$(OBJ))

all:
	make compile
compile:
	make $(OBJS)
	make test

test: $(OBJS)
	$(CXX) $(CXXFLAGS) -v -o test $(OBJS)

main.o: main.c
	$(CC) $(CFLAGS) -c -o main.o main.c

person.o: person.cpp
	$(CXX) $(CXXFLAGS) $(INCLUDE) -c -o person.o person.cpp

wrapper.o: wrapper.cpp
	$(CXX) $(CXXFLAGS) -c -o wrapper.o wrapper.cpp


clean:
	@ rm -rf $(OBJS) test *.o *.a