#
# Custom Makefile for illumos list_t functions.  See README.md for usage
# instructions.
#

BUILD_DIR	?= build
LIBFILE		 = $(BUILD_DIR)/illumos_list.a
OBJECTS		 = $(BUILD_DIR)/list.o
HEADERS		 = include/sys/list.h include/sys/list_impl.h
AR		?= ar

#
# list.c includes its own header file as sys/list.h, and we don't want local
# modifications, so we replicate the header tree under ./include.
#
CPPFLAGS	+= -I include

$(LIBFILE): $(OBJECTS)
	$(AR) rcs $@ $^

$(OBJECTS): $(BUILD_DIR)/%.o: src/%.c $(HEADERS) | $(BUILD_DIR)
	$(CC) -o $@ -c $(CPPFLAGS) $(CFLAGS) $<

$(BUILD_DIR):
	mkdir -p $@

clean:
	rm -f $(LIBFILE) $(OBJECTS)
