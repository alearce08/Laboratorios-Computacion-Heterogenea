CC := gcc
CFLAGS := -Wall -Wextra -O2 -fopenmp
LDLIBS := -lm

TARGETS := softmax_openmp matmul_tiled_openmp

THREADS ?= 4
SOFTMAX_REPETITIONS ?= 100000
MATMUL_REPETITIONS ?= 10
MATRIX_SIZE ?= 512
TILE_SIZE ?= 32

.PHONY: all run run-softmax run-matmul clean

all: $(TARGETS)

softmax_openmp: softmax_openmp.c
	$(CC) $(CFLAGS) $< -o $@ $(LDLIBS)

matmul_tiled_openmp: matmul_tiled_openmp.c
	$(CC) $(CFLAGS) $< -o $@ $(LDLIBS)

run: run-softmax

run-softmax: softmax_openmp
	./softmax_openmp $(THREADS) $(SOFTMAX_REPETITIONS)

run-matmul: matmul_tiled_openmp
	./matmul_tiled_openmp $(THREADS) $(MATRIX_SIZE) $(TILE_SIZE) $(MATMUL_REPETITIONS)

clean:
	rm -f $(TARGETS)