include /scratch/yc0769/benchmarks/gpu-rodinia/common/make.config

CC := $(CUDA_DIR)/bin/nvcc --cudart shared

INCLUDE := $(CUDA_DIR)/include

SRC = 3D.cu

EXE = 3D 

OUTPUT = *.out
#--gpu-architecture=compute_30 --gpu-code=compute_30arch sm_30
FLAGS = -arch sm_30 --ptxas-options=-v -lcudart
release: $(SRC)
	$(CC) $(KERNEL_DIM) $(FLAGS) $(SRC) -o $(EXE) -I$(INCLUDE) -L$(CUDA_LIB_DIR) 

enum: $(SRC)
	$(CC) $(KERNEL_DIM) $(FLAGS) -deviceemu $(SRC) -o $(EXE) -I$(INCLUDE) -L$(CUDA_LIB_DIR) 

debug: $(SRC)
	$(CC) $(KERNEL_DIM) $(FLAGS) -g $(SRC) -o $(EXE) -I$(INCLUDE) -L$(CUDA_LIB_DIR) 

debugenum: $(SRC)
	$(CC) $(KERNEL_DIM) $(FLAGS) -g -deviceemu $(SRC) -o $(EXE) -I$(INCLUDE) -L$(CUDA_LIB_DIR) 

clean: $(SRC)
	rm -f $(EXE) $(EXE).linkinfo $(OUTPUT) 
