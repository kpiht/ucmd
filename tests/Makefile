PROJ_NAME=ucmd
BUILD_DIR=build
TEST_DIR=.

SRCS=main.c
SRCS+=../err.c
SRCS+=$(TEST_DIR)/test_cmd.c
SRCS+=$(TEST_DIR)/test_utils.c
SRCS+=../utils.c
SRCS+=../ucmd.c

INC_DIRS=.
INC_DIRS+=../

CC=gcc
OBJCOPY=objcopy
OBJDUMP=objdump
SZ=size

# Any compiler options you need to set
CFLAGS=-ggdb3
CFLAGS+=-Og -Wall -Wextra -Warray-bounds

# Definition used for unit testing.
# Exposes static functions to testing framework.
DEFS=-DUNIT_TEST

INCLUDE = $(addprefix -I,$(INC_DIRS))

.PHONY: $(PROJ_NAME)
$(PROJ_NAME): $(PROJ_NAME).out

%.o: %.c
	$(CC) -c -o $@ $< $(CFLAGS)

$(PROJ_NAME).out: $(SRCS)
	mkdir -p $(BUILD_DIR)
	$(CC) $(INCLUDE) $(DEFS) $(CFLAGS) $^ -o $(BUILD_DIR)/$@

clean:
	rm -f *.o $(BUILD_DIR)/$(PROJ_NAME).*