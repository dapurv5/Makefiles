PROJECT := $(shell readlink $(dir $(lastword $(MAKEFILE_LIST))) -f)

CXX = g++
CXXFLAGS = -O3 \
           -std=c++11 \
           -Wall \
           -Wno-sign-compare \
           -fno-omit-frame-pointer

BIN_DIR = $(PROJECT)/bin
ANAHATA = $(BIN_DIR)/ANAHATA

#place all your header files only in a single folder, this still doesn't work with multiple folders  	  	
HEADER_FILES = $(shell find $(PROJECT)/src/main/native -type f -name "*.hpp"  -printf '%h\n' | sort -u)
CPP_FILES = $(shell find $(PROJECT)/src/main/native -type f -name "*.cpp")
OBJ_FILES = $(addprefix $(BIN_DIR)/,$(notdir $(CPP_FILES:.cpp=.o)))

BUILD_SRC = $(CPP_FILES:.cpp=.o)

LD_FLAGS = -lrt

INC_FLAGS = $(addprefix -I,$(HEADER_FILES))

all: path \
	 ANAHATA

path: $(BIN_DIR)

$(BIN_DIR):
	mkdir -p $@

$(ANAHATA): $(BUILD_SRC)
	$(CXX) $(OBJ_FILES) $(CXXFLAGS) $(LD_FLAGS) -o $@

$(BUILD_SRC): %.o: %.cpp $(HEADER_FILES)
	$(CXX) $(CXXFLAGS) $(INC_FLAGS) -c $< -o $(BIN_DIR)/$(shell basename $@)

ANAHATA: path $(ANAHATA)
	
clean:
	rm -rf $(BIN_DIR) $(OBJ_FILES)

.PHONY: all path ANAHATA clean
