# Secure and Minimal content-images, Epanet
# https://hub.docker.com/repository/docker/huggla/sam-content

# =========================================================================
# Init
# =========================================================================
# ARGs (can be passed to Build/Final) <BEGIN>
ARG SaM_VERSION="2.0.1"
ARG IMAGETYPE="content"
ARG EPANET_VERSION="2.00.12"
ARG HUBPROFILE="huggla"
ARG HUBREPO="epanet"
ARG HUBVERSION="$EPANET_VERSION"
ARG BASEIMAGE="huggla/secure_and_minimal:$SaM_VERSION-busybox"
ARG DOWNLOADS="https://www.epa.gov/sites/production/files/2018-10/en2source.zip"
ARG BUILDCMDS=\
"   unzip -o makefiles.ZIP "\
"&& mkdir epanet2 "\
"&& cd epanet2 "\
"&& unzip ../epanet2.zip "\
"&& unzip -o ../GNU_EXE.ZIP "\
"&& sed -i 's|//#define CLE|#define CLE|g' epanet.c "\
"&& sed -i 's|#define DLL|//#define DLL|g' epanet.c "\
"&& make -s "\
'&& mkdir -p "$DESTDIR/usr/bin" '\
'&& cp -a epanet2 "$DESTDIR/usr/bin/"'
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
