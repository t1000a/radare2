-include ../../config-user.mk

BINDIR=$(shell r2 -H R2_PREFIX)/bin
CWD=$(shell pwd)
V=v/v

all: $(V)
	$(V) -prod r2r.v
	#$(V) -g r2r.v

$(V): v
	cd v && git pull
	$(MAKE) -C v
	$(V) install radare.r2

fmt:
	$(V) fmt -w r2r.v

v:
	git clone https://github.com/vlang/v

install:
	v -prod r2r.v
	rm -f $(BINDIR)/r2r
	ln -fs $(CWD)/r2r $(shell r2 -H R2_PREFIX)/bin
	mkdir -p "${DESTDIR}${MANDIR}/man1"
	cp -rf r2r.1 "${DESTDIR}${MANDIR}/man1"