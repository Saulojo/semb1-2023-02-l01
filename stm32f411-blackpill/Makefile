dir_obj = build
dependencias = .deps
SRCS = src/startup.c \
       src/main.c

CFLAGS = -g -mcpu=cortex-m4 -mthumb -Wall -O0 -I./inc
DEPFLAGS = -MMD -MP -MF $(dependencias)/$*.d


OBJ = $(patsubst %, $(dir_obj)/%.o, $(basename $(SRCS)))
$(shell mkdir -p $(dir $(OBJ)) > /dev/null)

DEPS = $(patsubst %, $(dependencias)/%.d, $(basename $(SRCS)))
$(shell mkdir -p $(dir $(DEPS)) > /dev/null)
all: $(OBJ)

$(dir_obj)/%.o: %.c $(dependencias)/%.d
	$(CC) -c $(CFLAGS) $(DEPFLAGS) $< -o $@

$(DEPS):

-include $(DEPS)

.PHONY: clean
clean:
	$(RM) $(dir_obj) $(dependencias)
