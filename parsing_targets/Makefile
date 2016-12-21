#
# GNU Make version: 3.81
# Author: Robert "Chip" Senkbeil
#

.PHONY: _dev _prod _run __no_args % _%
.DEFAULT: %

#
# The handler for targets that are not defined.
# E.g. make something will look for _something that does not exist
#
_%:
	$(warning Unknown option: $*)

#
# The main implementation that looks for target1-target2-...
# to parse and run individually
#
.SECONDEXPANSION:
% : SHARED_VAR
% : $$(strip $$(foreach \
		flag,\
		$$(strip $$(subst -, , $$@)),\
		$$(if $$(findstring Makefile,$$(flag)),\
			,\
			_$$(flag)\
		)\
	))
	$(info ------------)
	$(info Received: $@)
	$(info Shared var: $(strip $(SHARED_VAR)))
	$(info Running main)
	$(info ------------)
	$(eval SHARED_VAR=) @# Reset at end to prevent crossover values

# Used as the catch-all if no target(s) provided to Make
__no_args:
	@echo "No target(s) provided to Make!"

# Represents a "flag" for Make
_dev:
	$(info Adding dev to shared variable)
	$(eval SHARED_VAR=$(SHARED_VAR) dev)

# Represents a "flag" for Make
_prod:
	$(info Adding prod to shared variable)
	$(eval SHARED_VAR=$(SHARED_VAR) prod)

# Represents a "flag" for Make
_run:
	$(info Adding run to shared variable)
	$(eval SHARED_VAR=$(SHARED_VAR) run)

