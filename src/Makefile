include ../build_config.mk

CFLAGS +=
OBJS = sim.o message.o decoder.o link.o handler.o server.o \
	fde.o log.o
LIB=libsim.a
HEADER_FILES=sim.h message.h decoder.h fde.h link.h handler.h server.h thread.h log.h strings.h

all: $(OBJS)
	mkdir -p $(HEADER_OUTPUT_DIR)
	ar -cru $(OUTPUT_DIR)/$(LIB) ${OBJS}
	cp $(HEADER_FILES) $(HEADER_OUTPUT_DIR)
	
fde.o: fde.h fde.cpp fde_select.cpp fde_epoll.cpp
	${CXX} ${CFLAGS} -c fde.cpp
.cpp.o:
	$(CXX) ${CFLAGS} -c $< -o $@

clean:
	rm -rf *.o *.a *.out $(OUTPUT_DIR)/$(LIB) $(HEADER_OUTPUT_DIR)

