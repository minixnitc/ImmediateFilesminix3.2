CFLAGS	= -D_MINIX -D_POSIX_SOURCE
SYS	= ../..
SERVERS = ../../servers
CCLD	= $(CC) -i $(CFLAGS)
CC	= exec cc

# This Makefile is large, but that is because it lists all actions that must
# be taken to compile and install all the simple commands.  If there were only
# one command then it would look like this:
#
# ALL	= \
#	cat \			need the 'cat' executable
#
# all:	$(ALL)			default rule, make all binaries
#
# cat:	cat.c			'cat' is made from 'cat.c'
#	$(CCLD) -o $@ $<	compile 'cat.c' ($<) to 'cat' ($@)
#	install -S 4kw $@	stack size is 8k (8086) or 16k (others)
#
# install:	\		rule to install all binaries
#	/usr/bin/cat \		one can find 'cat' in /usr/bin
#	/bin/cat \		important binaries are also in /bin
#
# /usr/bin/cat:	cat
#	install -cs -o bin $< $@	copy 'cat' to '/usr/bin/cat' (-c),
#					strip symbol table (-s)
#
# /bin/cat:	/usr/bin/cat
#	install -lcs $< $@	install '/bin/cat' by linking (if possible)
#				or copying (otherwise)
#
# Some of the binaries are installed under more than one name.  The extra
# names are indented by one extra tab in the install rule.
# If you want to add a command then insert it at the appropriate position
# in sorted order.  Search around for the command just above or below the
# the new command and add new rules for the new command near those places.
# Observe four key things:
#	What to make, how to make, what to install, how to install.

 ALL	= \
	dev2name \			# need the 'cat' executable

 all:	$(ALL)			# default rule, make all binaries

 dev2name:	dev2name.c			# 'cat' is made from 'cat.c'
	$(CCLD) -o $@ $<	# compile 'cat.c' ($<) to 'cat' ($@)
	install -S 4kw $@	# stack size is 8k (8086) or 16k (others)

 install:	\		# rule to install all binaries
	/usr/bin/dev2name \		#one can find 'cat' in /usr/bin
	/bin/dev2name \		# important binaries are also in /bin

 /usr/bin/dev2name:	dev2name
	install -cs -o bin $< $@	
	
 /bin/cat:	/usr/bin/dev2name
	install -lcs $< $@	
