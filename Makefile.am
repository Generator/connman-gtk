ACLOCAL_AMFLAGS = -I m4 ${ACLOCAL_FLAGS}
MANUAL_PAGES = doc/connman-gtk.1

desktopdir = $(datadir)/applications
desktop_DATA = connman-gtk.desktop

bin_PROGRAMS = connman-gtk
connman_gtk_SOURCES = src/main.c src/agent.c src/style.c src/technology.c \
		      src/service.c src/util.c src/settings.c src/status.c \
		      src/settings_content.c src/connection.c src/vpn.c \
		      src/wireless.c src/dialog.c src/config.c \
		      lib/openconnect_helper.c
connman_gtk_LDADD = @GTK_LIBS@ @GLib_LIBS@
connman_gtk_CPPFLAGS = @GTK_CFLAGS@ @GLib_CFLAGS@ \
		       -DCONNMAN_GTK_LOCALEDIR=\"${CONNMAN_GTK_LOCALEDIR}\" \
		       -DCONNMAN_GTK_UIDIR=\""$(uidir)"\" -I$(top_srcdir)/lib

EXTRA_DIST = src/agent.h src/interfaces.h src/main.h src/technology.h \
	     src/style.h src/service.h src/util.h src/settings.h src/status.h \
	     src/settings_content.h src/connection.h src/vpn.h src/wireless.h \
	     src/dialog.h src/config.h lib/openconnect_helper.h README.md \
	     net.connman.gtk.gschema.xml ${MANUAL_PAGES}

if USE_OPENCONNECT
connman_gtk_LDADD += @openconnect_LIBS@
connman_gtk_CPPFLAGS += @openconnect_CFLAGS@ -DUSE_OPENCONNECT=1
if USE_OPENCONNECT_DYNAMIC
connman_gtk_LDADD += -ldl
connman_gtk_CPPFLAGS += -DUSE_OPENCONNECT_DYNAMIC=1
endif
endif

if USE_STATUS_ICON
connman_gtk_CPPFLAGS += -DUSE_STATUS_ICON=1
endif

SUBDIRS = po

INTLTOOL_FILES = intltool-extract.in \
		 intltool-merge.in \
		 intltool-update.in

DISTCLEANFILES = intltool-extract \
		 intltool-merge \
		 intltool-update \
		 po/.intltool-merge-cache

gsettings_SCHEMAS = net.connman.gtk.gschema.xml
@GSETTINGS_RULES@

man_MANS = ${MANUAL_PAGES}
notrans_man_MANS = ${MANUAL_PAGES}
