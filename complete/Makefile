CXX=g++

CLANG_PREFIX=$(shell (cd /usr/local/include/clang-c/ && cd ../.. && pwd) 2> /dev/null || (cd /usr/lib/llvm-3.5/ && pwd) 2> /dev/null || (cd /usr/lib/llvm-3.4/ && pwd) 2> /dev/null || (cd /usr/lib/llvm-3.3/ && pwd) 2> /dev/null)
CLANG_FLAGS=-I$(CLANG_PREFIX)/include/
CLANG_LIBS=-L$(CLANG_PREFIX)/lib/ -Wl,-rpath=$(CLANG_PREFIX)/lib -lclang

FLAGS=$(CLANG_FLAGS)
LIBS=$(CLANG_LIBS)

LIB_NAME=libcomplete
SRC=complete

all:
	$(CXX) -std=gnu++0x $(FLAGS) -DNDEBUG -Os -c -fPIC complete.cpp -o $(SRC).o
	$(CXX) -shared -Wl,-soname,$(LIB_NAME).so -o $(LIB_NAME).so $(SRC).o $(LIBS)
debug:
	$(CXX) -std=gnu++0x $(FLAGS) -g -c -fPIC -DCLANG_COMPLETE_LOG $(SRC).cpp -o $(SRC).o
	$(CXX) -shared -Wl,-soname,$(LIB_NAME).so -o $(LIB_NAME).so $(SRC).o $(LIBS)
log:
	$(CXX) -std=gnu++0x $(FLAGS) -Os -c -fPIC -DCLANG_COMPLETE_LOG $(SRC).cpp -o $(SRC).o
	$(CXX) -shared -Wl,-soname,$(LIB_NAME).so -o $(LIB_NAME).so $(SRC).o $(LIBS)
