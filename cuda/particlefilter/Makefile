#makefile

include ../../common/make.config

CC := $(CUDA_DIR)/bin/nvcc

INCLUDE := $(CUDA_DIR)/include

all: naive float

naive: ex_particle_CUDA_naive_seq.cu
	$(CC) -I$(INCLUDE) -L$(CUDA_LIB_DIR) --cudart shared -O3 ex_particle_CUDA_naive_seq.cu -o particlefilter_naive -lcudart 
	
float: ex_particle_CUDA_float_seq.cu
	$(CC) -I$(INCLUDE) -L$(CUDA_LIB_DIR) --cudart shared -O3 ex_particle_CUDA_float_seq.cu -o particlefilter_float -lcudart -arch=sm_30

clean:
	rm particlefilter_naive particlefilter_float
