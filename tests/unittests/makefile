ifeq ($(OS),Windows_NT)
	EXT=.exe
	PLATFORM_OPTS=-static
	PLATFORM_LD_OPTS=-Wl,--no-as-needed
else
	UNAME_S := $(shell uname -s)
	ifeq ($(UNAME_S),Darwin)
		EXT=
		PLATFORM_OPTS=
		PLATFORM_LD_OPTS=
	else
		EXT=
		PLATFORM_OPTS=
		PLATFORM_LD_OPTS=-lrt -Wl,--no-as-needed
	endif
endif


default: unittests$(EXT)

unittests$(EXT): unittests.cpp ../../readerwriterqueue.h ../../atomicops.h ../common/simplethread.h ../common/simplethread.cpp minitest.h makefile
	g++ -static -std=c++11 -Wpedantic  -Wall -DNDEBUG -O0 -g unittests.cpp ../common/simplethread.cpp -o unittests$(EXT) -pthread -Wl,--no-as-needed,-u,pthread_cancel,-u,pthread_cond_broadcast,-u,pthread_cond_destroy,-u,pthread_cond_signal,-u,pthread_cond_wait,-u,pthread_create,-u,pthread_detach,-u,pthread_cond_signal,-u,pthread_equal,-u,pthread_join,-u,pthread_mutex_lock,-u,pthread_mutex_unlock,-u,pthread_once,-u,pthread_setcancelstate

run: unittests$(EXT)
	./unittests$(EXT)
