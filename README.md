# insanity
never thought ffmpeg could be such a learning experience


    ./configure --prefix=$HOME/custom/builds/gnutls --with-included-libtasn1 --with-included-unistring\
            LDFLAGS="-L$HOME/custom/builds/gmp/lib -L$HOME/custom/builds/nettle/lib64 -L$HOME/custom/builds/libev/lib -L$HOME/custom/builds/unbound/lib" \
            CPPFLAGS="-I$HOME/custom/builds/gmp/include -I$HOME/custom/builds/nettle/include -I$HOME/custom/builds/unbound/include"
#
    libtoolize



## .zshrc
    source /home/rsiah/custom/lib/docbook-xsl-1.79.1/.profile.incl
    export XML_CATALOG_FILES="$HOME/custom/etc/xml/catalog"
    export PKG_CONFIG_PATH="$HOME/custom/builds/nettle/lib64/pkgconfig:$HOME/custom/builds/gmp/lib/pkgconfig:$HOME/custom/builds/libtasn1/lib/pkgconfig:$HOME/custom/builds/p11-kit/lib/pkgconfig"



## catalog file
    <?xml version="1.0"?>
    <!DOCTYPE catalog PUBLIC "-//OASIS//DTD Entity Resolution XML Catalog V1.0//EN" "http://www.oasis-open.org/committees/entity/release/1.0/catalog.dtd">
    <catalog xmlns="urn:oasis:names:tc:entity:xmlns:xml:catalog">
  
    <rewriteSystem systemIdStartString="http://www.oasis-open.org/docbook/xml/4.5/" rewritePrefix="file:///home/rsiah/custom/lib/docbook-xml-4.5/"/>
    <rewriteURI uriStartString="http://www.oasis-open.org/docbook/xml/4.5/" rewritePrefix="file:///home/rsiah/custom/lib/docbook-xml-4.5/"/>
    <public publicId="-//OASIS//DTD DocBook XML V4.5//EN" uri="file:///home/rsiah/custom/lib/docbook-xml-4.5/docbookx.dtd"/>
  
    <rewriteSystem systemIdStartString="http://www.oasis-open.org/docbook/xml/4.4/" rewritePrefix="file:///home/rsiah/custom/lib/docbook-xml-4.5/"/>
    <rewriteURI uriStartString="http://www.oasis-open.org/docbook/xml/4.4/" rewritePrefix="file:///home/rsiah/custom/lib/docbook-xml-4.5/"/>
    <public publicId="-//OASIS//DTD DocBook XML V4.4//EN" uri="file:///home/rsiah/custom/lib/docbook-xml-4.5/docbookx.dtd"/>
  
    <rewriteSystem systemIdStartString="http://www.oasis-open.org/docbook/xml/4.3/" rewritePrefix="file:///home/rsiah/custom/lib/docbook-xml-4.5/"/>
    <rewriteURI uriStartString="http://www.oasis-open.org/docbook/xml/4.3/" rewritePrefix="file:///home/rsiah/custom/lib/docbook-xml-4.5/"/>
    <public publicId="-//OASIS//DTD DocBook XML V4.3//EN" uri="file:///home/rsiah/custom/lib/docbook-xml-4.5/docbookx.dtd"/>
  
    <rewriteSystem systemIdStartString="http://www.oasis-open.org/docbook/xml/4.2/" rewritePrefix="file:///home/rsiah/custom/lib/docbook-xml-4.5/"/>
    <rewriteURI uriStartString="http://www.oasis-open.org/docbook/xml/4.2/" rewritePrefix="file:///home/rsiah/custom/lib/docbook-xml-4.5/"/>
    <public publicId="-//OASIS//DTD DocBook XML V4.2//EN" uri="file:///home/rsiah/custom/lib/docbook-xml-4.5/docbookx.dtd"/>
  
    <rewriteSystem systemIdStartString="http://docbook.sourceforge.net/release/xsl/current/" rewritePrefix="file:///home/rsiah/custom/lib/docbook-xsl-1.79.1/"/>
    <rewriteURI uriStartString="http://docbook.sourceforge.net/release/xsl/current/" rewritePrefix="file:///home/rsiah/custom/lib/docbook-xsl-1.79.1/"/>
  
    </catalog>

And then ./autogen.sh --path flag here --with-xml-catalog=/path/to/catalog

the file is literally called catalog not sure if it needs to be called that though
## AC_DEFINE erroR??!?

Is pkg.m4 inside the source's m4 dir? PROBABLY NOT

M4 too OLD??

JUST DOWNGRADE BRUH IT'S NOT WORTH IT TRYING TO INSTALL PKGCONFIG (though I did but didn't use it because I just downgraded)

need vorbis need ogg need lame I give up on av1 and vp9

ffmpeg

    cd ~/ffmpeg_sources && \
    wget -O ffmpeg-snapshot.tar.bz2 https://ffmpeg.org/releases/ffmpeg-snapshot.tar.bz2 && \
    tar xjvf ffmpeg-snapshot.tar.bz2 && \
    cd ffmpeg && \
    PATH="$HOME/bin:$PATH" ./configure \
      --prefix="$HOME/ffmpeg_build" \
      --pkg-config-flags="--static" \
      --extra-cflags="-I$HOME/ffmpeg_build/include -I$HOME/custom/builds/gnutls/include -I$HOME/custom/builds/p11-kit/include/p11-kit-1 -I$HOME/custom/builds/nettle/include -I$HOME/custom/builds/gmp/include -I$HOME/custom/builds/libass/include -I$HOME/custom/builds/lame/include" \
      --extra-ldflags="-L$HOME/ffmpeg_build/lib -L$HOME/custom/builds/gnutls/lib -L$HOME/custom/builds/p11-kit/lib -L$HOME/custom/builds/nettle/lib64 -L$HOME/custom/builds/gmp/lib -L$HOME/custom/builds/libass/lib -L$HOME/custom/builds/lame/lib" \
      --extra-libs="-lpthread -lm" \
      --ld="g++" \
      --bindir="$HOME/bin" \
      --enable-gpl \
      --enable-gnutls \
      --enable-libass \
      --enable-libfdk-aac \
      --enable-libfreetype \
      --enable-libmp3lame \
      --enable-libopus \
      --enable-libvorbis \
      --enable-libx264 \
      --enable-libx265 \
      --enable-nonfree && \
    PATH="$HOME/bin:$PATH" make && \
    make install && \
    hash -r
