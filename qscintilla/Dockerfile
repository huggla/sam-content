# Secure and Minimal content-images, Qscintilla
# https://hub.docker.com/repository/docker/huggla/sam-content

# =========================================================================
# Init
# =========================================================================
# ARGs (can be passed to Build/Final) <BEGIN>
ARG SaM_VERSION="2.0.4"
ARG IMAGETYPE="content"
ARG QSCINTILLA_VERSION="2.11.5"
ARG HUBPROFILE="huggla"
ARG HUBREPO="qscintilla"
ARG HUBVERSION="$QSCINTILLA_VERSION"
ARG BASEIMAGE="huggla/secure_and_minimal:$SaM_VERSION-busybox"
ARG ADDREPOS="http://dl-cdn.alpinelinux.org/alpine/edge/testing"
ARG BUILDDEPS="build-base libtool qt5-qtbase-dev py3-sip-pyqt5 py3-sip py3-qtpy py-sip-dev python3-dev fortify-headers py3-qt5"
ARG DOWNLOADS="https://www.riverbankcomputing.com/static/Downloads/QScintilla/$QSCINTILLA_VERSION/QScintilla-$QSCINTILLA_VERSION.tar.gz"
ARG BUILDCMDS=\
"   cd QScintilla-$QSCINTILLA_VERSION/Qt4Qt5 "\
"&& qmake-qt5 "\
'&& eval "$COMMON_MAKECMDS" '\
"&& cd ../Python "\
"&& python3 configure.py --pyqt=PyQt5 --qmake=/usr/bin/qmake-qt5 --no-docstrings "\
'&& eval "$COMMON_MAKECMDS" '\
"&& cd / "\
"&& cp -a \$BUILDDIR \$DESTDIR/ "\
'&& apk --repositories-file /etc/apk/repositories --keys-dir /etc/apk/keys --no-cache --initramfs-diskless-boot --clean-protected --root $DESTDIR add --initdb '$BUILDDEPS\
'&& chroot "$DESTDIR" /bin/sh -c "cd \"$BUILDDIR/QScintilla-'"$QSCINTILLA_VERSION"'/Qt4Qt5\" && make install" '\
'&& chroot "$DESTDIR" /bin/sh -c "cd \"$BUILDDIR/QScintilla-'"$QSCINTILLA_VERSION"'/Python\" && make install" '\
'&& apk --repositories-file /etc/apk/repositories --keys-dir /etc/apk/keys --no-cache --initramfs-diskless-boot --clean-protected --root $DESTDIR --purge del '$BUILDDEPS\
"&& rm -rf \$DESTDIR\$BUILDDIR"
# ARGs (can be passed to Build/Final) </END>

# Generic template (don't edit) <BEGIN>
FROM ${CONTENTIMAGE1:-scratch} as content1
FROM ${CONTENTIMAGE2:-scratch} as content2
FROM ${CONTENTIMAGE3:-scratch} as content3
FROM ${CONTENTIMAGE4:-scratch} as content4
FROM ${CONTENTIMAGE5:-scratch} as content5
FROM ${INITIMAGE:-${BASEIMAGE:-huggla/secure_and_minimal:$SaM_VERSION-base}} as init
# Generic template (don't edit) </END>

# =========================================================================
# Build
# =========================================================================
# Generic template (don't edit) <BEGIN>
FROM ${BUILDIMAGE:-huggla/secure_and_minimal:$SaM_VERSION-build} as build
FROM ${BASEIMAGE:-huggla/secure_and_minimal:$SaM_VERSION-base} as final
COPY --from=build /finalfs /
# Generic template (don't edit) </END>

# =========================================================================
# Final
# =========================================================================
# Generic template (don't edit) <BEGIN>
USER starter
ONBUILD USER root
# Generic template (don't edit) </END>
