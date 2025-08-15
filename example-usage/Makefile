src_dir = ..
common_sources = ${src_dir}/sensirion_config.h ${src_dir}/sensirion_common.h ${src_dir}/sensirion_common.c ${src_dir}/sensirion_streaming.c
uart_sources = ${src_dir}/sensirion_uart_hal.h ${src_dir}/sensirion_shdlc.h ${src_dir}/sensirion_shdlc.c ${src_dir}/sensirion_streaming_shdlc.c
driver_sources = ${src_dir}/sps30_uart.h ${src_dir}/sps30_uart.c

uart_implementation ?= ${src_dir}/sensirion_uart_hal.c

CFLAGS = -Os -Wall -fstrict-aliasing -Wstrict-aliasing=1 -Wsign-conversion -fPIC -I${src_dir} -I.

ifdef CI
    CFLAGS += -Werror
endif

.PHONY: all clean

all: sps30_uart_example_usage

sps30_uart_example_usage: clean
	$(CC) $(CFLAGS) -o $@  ${driver_sources} ${uart_sources} \
		${uart_implementation} ${common_sources} sps30_uart_example_usage.c

clean:
	$(RM) sps30_uart_example_usage