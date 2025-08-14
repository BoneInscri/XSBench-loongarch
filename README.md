**修改如下：**

```
ifeq ($(CC),)
# CC    = gcc
CC    = loongarch64-linux-gnu-gcc
endif

ifeq (cc,$(CC))
# CC    = gcc
CC      = loongarch64-linux-gnu-gcc
endif

# Standard Flags
# CFLAGS := -std=gnu99 -Wall
CFLAGS := -std=gnu99 -Wall -march=loongarch64 -mabi=lp64d

# Linker Flags
# LDFLAGS = -lm
LDFLAGS = -lm -static
```



1. **编译，构建项目**

```
cd openmp-threading
make
```

```
./
├── GridInit.c
├── GridInit.o
├── io.c
├── io.o
├── Main.c
├── Main.o
├── Makefile
├── Materials.c
├── Materials.o
├── Simulation.c
├── Simulation.o
├── XSBench
├── XSbench_header.h
├── XSutils.c
└── XSutils.o
```

2. **测试命令**

```
./XSBench -m history -s small
```

```
[root@dedsec testbench]#                
================================================================================
                   __   __ ___________                 _                        
                   \ \ / //  ___| ___ \               | |                       
                    \ V / \ `--.| |_/ / ___ _ __   ___| |__                     
                    /   \  `--. \ ___ \/ _ \ '_ \ / __| '_ \                    
                   / /^\ \/\__/ / |_/ /  __/ | | | (__| | | |                   
                   \/   \/\____/\____/ \___|_| |_|\___|_| |_|                   

================================================================================
                    Developed at Argonne National Laboratory
                                   Version: 20
================================================================================
                                  INPUT SUMMARY
================================================================================
Simulation Method:            History Based
Grid Type:                    Unionized Grid
Materials:                    12
H-M Benchmark Size:           small
Total Nuclides:               68
Gridpoints (per Nuclide):     11,303
Unionized Energy Gridpoints:  768,604
Particle Histories:           500,000
XS Lookups per Particle:      34
Total XS Lookups:             34
Threads:                      1
Est. Memory Usage (MB):       241
Binary File Mode:             Off
================================================================================
                         INITIALIZATION - DO NOT PROFILE
================================================================================
Intializing nuclide grids...
Intializing unionized grid...
Intializing material data...
Intialization complete. Allocated 240 MB of data.

================================================================================
                                   SIMULATION
================================================================================
Beginning history based simulation...

Simulation complete.
================================================================================
                                     RESULTS
================================================================================
Threads:     1
Runtime:     67.919 seconds
Lookups:     17,000,000
Lookups/s:   250,298
Verification checksum: 941535 (Valid)
================================================================================
```

```
# 默认命令
./XSBench
```



