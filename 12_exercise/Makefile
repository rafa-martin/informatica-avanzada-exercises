TARGET = main

SRCS  = $(shell find ./src -type f -name *.cpp)
HEADS = $(shell find ./inc -type f -name *.hpp)
OBJS = $(SRCS:.cpp=.o)
DEPS = Makefile.depend

INCLUDES = -I./inc
CPPFLAGS = -std=c++17 -O2 -Wall $(INCLUDES)
LDFLAGS = -lm

all: $(TARGET)

$(TARGET): $(OBJS) $(HEADS)
	$(CXX) $(LDFLAGS) -o $@ $(OBJS)

run: all
	@./$(TARGET)

.PHONY: depend clean
depend:
	$(CXX) $(INCLUDES) -MM $(SRCS) > $(DEPS)
	@sed -i -E "s/^(.+?).o: ([^ ]+?)\1/\2\1.o: \2\1/g" $(DEPS)

clean:
	$(RM) $(OBJS) $(TARGET)

-include $(DEPS)