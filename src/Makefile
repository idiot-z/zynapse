# Update the following lines to your system requirements
AURYNPATH=$(HOME)/auryn

# Path to Auryn include files
AURYNINC=$(AURYNPATH)/src

# Path to Auryn library
AURYNLIB=$(AURYNPATH)/build/release/src



# The following should not require updating in most cases 
CC = mpic++
CFLAGS=-ansi -pipe -O3 -march=native -ffast-math -pedantic -I/usr/include -I$(AURYNINC)
LDFLAGS=$(AURYNLIB)/libauryn.a -lboost_filesystem -lboost_system -lboost_program_options -lboost_mpi -lboost_serialization 

SIMFILES=sim_frey
OBJFILES=ZynapseConnection.o ZynapseMonitor.o PRPGroup.o

simfiles: $(SIMFILES)

sim_%: sim_%.o $(OBJFILES) 
	$(CC) $(CFLAGS) $^ $(LDFLAGS) -o $(subst .o,,$<)

%.o : %.cpp
	$(CC) $(CFLAGS) -c $<

clean:
	rm -f *~ *.o core a.out *.log *.a $(SIMFILES)

