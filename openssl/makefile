# Simple general purpose makefile
# project: ed25519demo
# written by ToraNova
# chia_jason96@live.com
#
# !NOTE!
# This makefile is suitable for one source demo projects
# only. not intermediary object files are compiled by this

# DIR-STRUCTURE DECLARES
BINDIR   = bin
MAINDIR = src
IDIR = include

# create targets
MAINS := $(wildcard $(MAINDIR)/*.c)
MAINP := $(MAINS:$(MAINDIR)/%.c=$(BINDIR)/%)

# read more :https://stackoverflow.com/questions/10906275/undefined-reference-to-stdios-baseinitinit
#CC = gcc
CC = g++
ls = ls
rm = rm

#CLIBS = -lstdc++ -lm -lpthread -lrt -maes -msse4 -lmsgpackc -lcrypto -lgnutlsxx -lgnutls -lssl
CLIBS = -lcrypto
CFLAGS= -O3 -Wall -march=native -I$(IDIR)

# default target
.PHONY: all mains
all:	mains
	@echo 'make done'
	@$(ls) $(BINDIR)

mains: $(MAINP)

$(MAINP) : $(BINDIR)/%: $(MAINDIR)/%.c
	$(CC) $< -o $@ $(CLIBS) $(CFLAGS)

# utils - cleanup
.PHONEY: clean
clean:
	@echo "Clearing builds..."
	@$(rm) $(BINDIR)/*
