all: anahata

anahata: main.o
	g++ build/main.o -o build/anahata

main.o:
	g++ -c src/main/native/src/*.cpp -o build/main.o




### Play ###############

#shm_open is made available by linking librt.
play: play.o boost.o
	g++ build/play.o build/boost.o -o build/anahata -lrt
play.o:
	g++ -c src/play/native/src/*.cpp -o build/play.o

boost.o:
	g++ -L/usr/lib/x86_64-linux-gnu -c src/play/cpp/boost/*.cpp -o build/boost.o
