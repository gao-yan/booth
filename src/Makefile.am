MAINTAINERCLEANFILES	= Makefile.in

AM_CFLAGS		= -fPIC -Werror

INCLUDES		= -I$(top_builddir)/include

sbin_PROGRAMS		= boothd

boothd_SOURCES	 	= config.c main.c paxos.c ticket.c  transport.c \
			  pacemaker.c paxos_lease.c timer.c

boothd_LDADD	  	= -lplumb -lplumbgpl
boothd_LDFLAGS		= $(OS_DYFLAGS) -L./

noinst_HEADERS		= booth.h list.h pacemaker.h paxos_lease.h timer.h \
			  config.h log.h paxos.h ticket.h transport.h

if HAVE_HELP2MAN
man_MANS		= booth.8 boothd.8
MAINTAINERCLEANFILES	+= $(man_MANS)
EXTRA_DIST		= $(man_MANS)

%.8: %
	$(HELP2MAN) -N -o $@ ./$<
endif

lint:
	-splint $(INCLUDES) $(LINT_FLAGS) $(CFLAGS) *.c
