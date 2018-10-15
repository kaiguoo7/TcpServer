APP = TcpServer

DB_INCLUDE = -I./
DB_INCLUDE += -I/usr/include
DB_CFLAGS += $(DB_INCLUDE) -g 
LIB= -L/usr/lib -ljson-c -lpthread
BUILD_DIR = ./build
OBJSDIR = ./build/obj


VPATH += debug:db:cfg:tools.
SRCDIRS += debug db cfg tools .

SRCFILES = $(foreach dir,$(SRCDIRS),$(wildcard $(dir)/*.c))
SRCFILENAMES = $(notdir $(SRCFILES))
OBJS = $(patsubst %.c, %.o,$(SRCFILENAMES))

ELF_FILE = $(BUILD_DIR)/$(APP).elf
MAP_FILE = $(BUILD_DIR)/$(APP).map.sym

build: make-dir $(OBJSDIR) $(OBJS) $(TARDIR)
	$(CC) -o $(ELF_FILE) $(OBJSDIR)/*.o $(LINKFLAGS) $(LIB)

$(OBJS): %.o:%.c
	$(CC) -c $(CFLAGS) $(DB_CFLAGS) $< -o $(OBJSDIR)/$@

.PHONY: make-dir
make-dir:
	@mkdir -p $(BUILD_DIR)
	@mkdir -p $(OBJSDIR)

.PHONY: clean
clean:
	rm -rf $(BUILD_DIR)
