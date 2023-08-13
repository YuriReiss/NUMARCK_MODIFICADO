CC = mpicc
OPTS = -O2
CFLAGS = $(OPTS)

HDF5_LIBS = -lhdf5_hl -lhdf5
COMM_LIBS = -lz -lm

LIBS = $(HDF5_LIBS) $(COMM_LIBS)

.c.o:
	$(CC) $(CFLAGS) -c $<

comp_hdf5 : mpi_compress.o mpi_kmeans.o memory_bit_buffer.o
	$(CC) -D_ADD_HDF5_ -o $@ $^ $(LIBS)

decomp_hdf5 : mpi_decompress.o memory_bit_buffer.o
	$(CC) -D_ADD_HDF5_ -o $@ $^ $(LIBS)

clean:
	rm -f *.o comp_hdf5 decomp_hdf5
