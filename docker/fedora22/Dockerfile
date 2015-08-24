FROM fedora:22
MAINTAINER Igor Gnatenko <i.gnatenko.brain@gmail.com>

RUN dnf install buildbot-slave -y
RUN useradd -m -d /var/lib/buildbot buildbot

RUN dnf install -y \
 ninja-build \
 gcc gcc-c++ gcc-gfortran gcc-objc gcc-objc++ java-devel mono-core mono-devel vala \
 boost-devel \
 gtest-devel \
 gmock-devel \
 qt5-qtbase-devel \
 wxGTK3-devel \
 flex bison \
 gettext \
 gnustep-base-devel \
 git-core \
 "pkgconfig(protobuf)" \
 "pkgconfig(glib-2.0)" \
 "pkgconfig(gobject-introspection-1.0)" \
 "pkgconfig(zlib)"

USER buildbot
WORKDIR /var/lib/buildbot
RUN buildslave create-slave . ci.mesonbuild.com fedora22 buildslave

ENTRYPOINT ["/usr/bin/buildslave"]
CMD ["start", "--nodaemon"]
