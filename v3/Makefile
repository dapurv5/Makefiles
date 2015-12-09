PROJECT := $(shell readlink $(dir $(lastword $(MAKEFILE_LIST))) -f)

CXX = g++
CXXFLAGS = -O3 \
           -std=c++11 \
           -Wall \
           -Wno-sign-compare \
           -fno-omit-frame-pointer


#place all your header files only in a single folder, this still doesn't work with multiple folders  	  	
ANAHATA_HEADERS = $(shell find $(PROJECT)/src/main/native -type f -name "*.hpp"  -printf '%h\n' | sort -u)
ANAHATA_SRC     = $(shell find $(PROJECT)/src/main/native -type f -name "*.cpp")
ANAHATA_OBJ = $(ANAHATA_SRC:.cpp=.o)

LD_FLAGS = -lrt
INC_FLAGS = -I$(ANAHATA_HEADERS) 

BIN_DIR = $(PROJECT)/bin
ANAHATA = $(BIN_DIR)/ANAHATA

all: path \
	 ANAHATA

path: $(BIN_DIR)

$(BIN_DIR):
	mkdir -p $@

$(ANAHATA): $(ANAHATA_OBJ)
	$(CXX) $(ANAHATA_OBJ) $(CXXFLAGS) $(LD_FLAGS) -o $@

$(ANAHATA_OBJ): %.o: %.cpp $(ANAHATA_HEADERS)
	$(CXX) $(CXXFLAGS) $(INC_FLAGS) -c $< -o $@

ANAHATA: path $(ANAHATA)
	
clean:
	rm -rf $(BIN_DIR) $(ANAHATA_OBJ)

.PHONY: all path ANAHATA clean
