# build leafony develop image
.PHONY: image
image:
	docker build . -t leafony-dev

.PHONY: start
start:
	docker run -it -v ${PWD}:/src leafony-dev bash

# detect leafony device file
.PHONY: detect
detect:
	ls /dev/cu.usb*

.PHONY: build
build:
	docker run --rm -v ${PWD}:/src leafony-dev cargo build


.PHONY: write
write: ./target/avr-atmega328p/debug/lefony.elf
	avrdude -patmega328p -carduino -P${DEVICE} -b57600 -D -U flash:w:./target/avr-atmega328p/debug/lefony.elf:e
