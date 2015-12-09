IDIR=src/main/native/include
SRC_DIR=src/main/native/src
CC=g++ -g
CFLAGS=-I$(IDIR)

STINGER_FOLDER=/home/dapurv5/MyCode/hpc-projects/stinger
STINGER_INCLUDE=$(STINGER_FOLDER)/build/include/stinger_core/
STINGER_LIBS=-I$(STINGER_INCLUDE) -L$(STINGER_FOLDER)/build/lib/

LIBS=-lrt -lstinger_core $(STINGER_LIBS) 
ODIR=build

_DEPS = boost_example.hpp
DEPS = $(patsubst %,$(IDIR)/%,$(_DEPS))

_OBJ = main.o boost_example.o stinger_example.o struct_sort_example.o \
       memcopy_example.o compress_decompress_example.o
OBJ = $(patsubst %,$(ODIR)/%,$(_OBJ))

all: $(ODIR)/anahata

$(ODIR)/anahata: $(OBJ)
	$(CC) -o $@ $^ $(CFLAGS) $(LIBS)

#This compiles all .cpp files to .o files	
$(ODIR)/%.o: $(SRC_DIR)/%.cpp $(DEPS)
	$(CC) -c -o $@ $< $(CFLAGS) -I$(STINGER_INCLUDE)
	
clean:
	rm -f $(ODIR)/*.o $(ODIR)/anahata

