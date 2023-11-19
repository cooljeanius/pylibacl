
ACLOCAL_AMFLAGS = -I m4 --install

AUTOMAKE_OPTIONS = foreign

SPHINXOPTS    = -W
SPHINXBUILD   = @SPHINX_BUILD@
DOCDIR        = doc
DOCHTML       = $(DOCDIR)/html
DOCTREES      = $(DOCDIR)/doctrees
ALLSPHINXOPTS = -d $(DOCTREES) $(SPHINXOPTS) $(DOCDIR)

MODNAME = posix1e.@SO_SUFFIX@
RSTFILES = doc/index.rst doc/module.rst NEWS README doc/conf.py

DISTCLEANFILES = *~

all: doc test

$(MODNAME): acl.c
	@PYTHON@ ./setup.py build_ext --inplace

$(DOCHTML)/index.html: $(MODNAME) $(RSTFILES)
	$(SPHINXBUILD) -b html $(ALLSPHINXOPTS) $(DOCHTML)
	touch $@

doc: $(DOCHTML)/index.html

dist-local:
	$(FAKEROOT) ./setup.py sdist
.PHONY: dist-local

test:
	$(AM_V_at)for ver in 2.4 2.5 2.6 2.7 3.0 3.1 3.2 3.3 3.4; do \
	  if type python$${ver} >/dev/null 2>/dev/null; then \
	    if test -x "`which python$${ver} 2>/dev/null`"; then \
	      echo "Testing with python$${ver}"; \
	      python$${ver} ./setup.py test -q || python$${ver} -m py_compile ./setup.py; \
	    else \
	      echo "Cannot test with python$${ver}"; \
	    fi; \
	  else \
	    echo "python$${ver} is missing"; \
	  fi; \
	done
	$(AM_V_at)if type pypy >/dev/null 2>/dev/null; then \
	  echo "Testing with pypy"; \
	  pypy ./setup.py test -q; \
	else \
	  echo "pypy is missing"; \
	fi

clean-local:
	rm -rf $(DOCHTML) $(DOCTREES)
	rm -f $(MODNAME)
	rm -f *.so
	rm -rf build

distclean-local:
	-rm -rf autom4te.cache || rmdir autom4te.cache

.PHONY: doc test clean-local
