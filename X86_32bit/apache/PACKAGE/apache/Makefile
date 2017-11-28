first_rule: all

all: build install

PACKAGE_VERSION := httpd-2.4.29
PACKAGE_DIR := httpd-2.4.29

# Configuration
PACKAGE_CONF := \
    --prefix=$(CURDIR)/../../OBJ/ \
    CFLAGS=-m32 \
    CXXFLAGS=-m32 \
    LDFLAGS=-m32 \
    --build=x86_64-pc-linux-gnu \
    --host=i686-pc-linux-gnu \
    ap_cv_void_ptr_lt_long=4 \

test_directory: 
	if [ ! -d $(CURDIR)/../../TARGET ]; then \
	   mkdir $(CURDIR)/../../TARGET/; \
	fi
	if [ -d $(CURDIR)/../../TARGET/$(PACKAGE_DIR) ]; then \
	       echo "Folder existed"; \
	else \
	       tar xvf $(CURDIR)/$(PACKAGE_DIR).tar.bz2 -C $(CURDIR)/../../TARGET/; \
	fi

build_lib: test_directory
	cd $(CURDIR)/../../TARGET/$(PACKAGE_DIR) && ./configure $(PACKAGE_CONF); \
	
build: build_lib
	$(MAKE) -C $(CURDIR)/../../TARGET/$(PACKAGE_DIR) all

pre_install_check:
	if [ ! -d $(CURDIR)/../../OBJ/bin ]; then \
	    mkdir -p $(CURDIR)/../../OBJ/bin; \
	fi


install: pre_install_check
	$(MAKE) -C $(CURDIR)/../../TARGET/$(PACKAGE_DIR) install; \

config_rule:

clean_rule:

uninstall_rule:

