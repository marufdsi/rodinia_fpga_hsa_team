include ../common/make.config
OPENCL_INC=/opt/altera/16.0/hld/host/include/
OPENCL_LIB=/opt/altera/16.0/hld/host/linux64/lib/

# C compiler
CC = g++
CC_FLAGS = -g -O2 -std=c++11

FPGA_SRC = cluster.o getopt.o read_input.o kmeans_clustering.o rmse.o

all :       kmeans_fpga.exe


kmeans_fpga.exe: $(FPGA_SRC)
	$(CC) $(KERNEL_DIM) $(CC_FLAGS) -lOpenCL kmeans_fpga.cpp $(FPGA_SRC) -o $@ -I$(OPENCL_INC) -L$(OPENCL_LIB) -lOpenCL

%.o: %.[ch]
	$(CC) $(CC_FLAGS) $< -c

cluster.o: cluster.c 
	$(CC) $(CC_FLAGS) cluster.c -c

getopt.o: getopt.c 
	$(CC) $(CC_FLAGS) getopt.c -c

kmeans.o: kmeans.c 
	$(CC) $(CC_FLAGS) read_input.c -c

rmse.o: rmse.c
	$(CC) $(CC_FLAGS) rmse.c -c

clean:
	rm -f *.o *~ kmeans *.linkinfo *.exe
