#!/usr/bin/make -f
SHELL:=/bin/bash


regions:=$(shell tail -n +2 dwr_list.csv | cut -d, -f 2 | tr  :upper: :lower:)

files:=$(patsubst %,http://www.water.ca.gov/landwateruse/docs/landusedata/shapes/%.zip,${regions})

info:
	@echo ${files}

.PHONY:mirror

mirror:
	wget -v --mirror --include-directories=landwateruse/docs/landusedata/shapes/ --exclude-directories=* http://www.water.ca.gov/landwateruse/lusrvymain.cfm

unzip:
	for z in www.water.ca.gov/landwateruse/docs/landusedata/shapes/*.zip; do d=`basename $z .zip`; mkdir $d; (cd data/$d; unzip ../../$z) ; done
	for d in (cd data echo *); do (cd data/$d; mv $d/* .; rmdir $d); done

