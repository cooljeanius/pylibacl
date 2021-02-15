
ACLOCAL_AMFLAGS = -I m4 --install

SPHINXOPTS    = -W
SPHINXBUILD   = @SPHINX_BUILD@
DOCDIR        = doc
DOCHTML       = $(DOCDIR)/html
DOCTREES      = $(DOCDIR)/doctrees
ALLSPHINXOPTS = -d $(DOCTREES) $(SPHINXOPTS) $(DOCDIR)

MODNAME = posix1e.@SO_SUFFIX@
RSTFILES = doc/index.rst doc/module.rst NEWS README doc/conf.py

all: doc test

$(MODNAME): acl.c
	@PYTHON@ ./setup.py build_ext --inplace

$(DOCHTML)/index.html: $(MODNAME) $(RSTFILES)
	$(SPHINXBUILD) -b html $(ALLSPHINXOPTS) $(DOCHTML)
	touch $@

doc: $(DOCHTML)/index.html

test:
	for ver in 2.4 2.5 2.6 2.7 3.0 3.1 3.2; do \
	  if type python$$ver >/dev/null; then \
	    echo Testing with python$$ver; \
	    python$$ver ./setup.py test; \
          fi; \
	done

clean-local:
	rm -rf $(DOCHTML) $(DOCTREES)
	rm -f $(MODNAME)
	rm -rf build

.PHONY: doc test clean-local
