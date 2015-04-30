ifeq ($(OS),Windows_NT)
	EXT = .exe
else
	EXT =
endif


default: stabtest$(EXT)

stabtest$(EXT): stabtest.cpp ../../readerwriterqueue.h ../../atomicops.h ../common/simplethread.h ../common/simplethread.cpp makefile
	g++ -static -std=c++11 -Wpedantic  -Wall -DNDEBUG -O3 stabtest.cpp ../common/simplethread.cpp -o stabtest$(EXT) -pthread -Wl,--no-as-needed,-u,pthread_cancel,-u,pthread_cond_broadcast,-u,pthread_cond_destroy,-u,pthread_cond_signal,-u,pthread_cond_wait,-u,pthread_create,-u,pthread_detach,-u,pthread_cond_signal,-u,pthread_equal,-u,pthread_join,-u,pthread_mutex_lock,-u,pthread_mutex_unlock,-u,pthread_once,-u,pthread_setcancelstate

run: stabtest$(EXT)
	./stabtest$(EXT)
