AM_CPPFLAGS = -I$(top_srcdir)/src/libs -I$(top_builddir)/src/libs $(gwenhywfar_includes) -I$(srcdir)/../../../ -I$(srcdir)/../../

AM_CFLAGS=-DBUILDING_AQBANKING @visibility_cflags@


typefiles=


dlgdatadir=$(aqbanking_pkgdatadir)/backends/aqofxconnect/dialogs
dlgdata_DATA=


build_sources=

build_headers_priv=


build_headers_pub=

build_headers=$(build_headers_priv) $(build_headers_pub)


noinst_HEADERS=$(build_headers_priv) $(build_headers_pub) \
  io_network.h \
  n_acctinfo.h \
  n_signon.h \
  n_statement.h \
  n_utils.h



#iheaderdir=@aqbanking_headerdir_am@/aqofxconnect
#iheader_HEADERS=


noinst_LTLIBRARIES=libofxdccommon.la
libofxdccommon_la_SOURCES= $(build_sources) \
  io_network.c \
  n_acctinfo.c \
  n_signon.c \
  n_statement.c \
  n_utils.c


EXTRA_DIST=$(typefiles) $(dlgdata_DATA) $(dlgimage_DATA) $(build_sources) $(build_headers)


built_sources: $(build_sources)



sources:
	for f in $(libofxdccommon_la_SOURCES); do \
	  echo $(subdir)/$$f >>$(top_srcdir)/i18nsources; \
	done
	for f in $(dlgdata_DATA); do \
	  echo $(subdir)/$$f >>$(top_srcdir)/dlgsources; \
	done
	for d in $(SUBDIRS); do \
	  $(MAKE) -C $$d sources; \
	done




cppcheck:
	for f in $(libofxdccommon_la_SOURCES); do \
	  cppcheck --force $$f ; \
	done
	for d in $(SUBDIRS); do \
	  $(MAKE) -C $$d cppcheck; \
	done


typefiles: $(typefiles)
	$(typemaker2_exe) -I $(top_srcdir)/src/libs/aqbanking/typemaker2/c -I $(gwenhywfar_dir)/share/gwenhywfar/typemaker2/c -I $(srcdir) --destfolder="$(srcdir)" $(typefiles)

typedefs: $(typefiles)
	$(typemaker2_exe) --defs-only -I $(top_srcdir)/src/libs/aqbanking/typemaker2/c -I $(gwenhywfar_dir)/share/gwenhywfar/typemaker2/c -I $(srcdir) --destfolder="$(srcdir)" $(typefiles)

