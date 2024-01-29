
# nftables build

This project contains a copy of libmnl, libnftnl and nftables which are built and the resultant nft binary is exported.

### Project Dependencies
- libmnl
  - https://www.netfilter.org/projects/libmnl/files/libmnl-1.0.5.tar.bz2
  - Source is extracted to: `<repo root>/libmnl`
- libnftnl
    - https://www.netfilter.org/projects/libnftnl/files/libnftnl-1.2.6.tar.xz
    - Source is extracted to: `<repo root>/libnftnl`
- nftables
    - https://www.netfilter.org/projects/nftables/files/nftables-1.0.9.tar.xz
    - Source is extracted to: `<repo root>/nftables`

#### netfilter

Project URL: https://netfilter.org

The netfilter project provides packet filtering software for the Linux 2.4.x and later kernel series.

## Sophos build instructions
1. Clone this repo
2. Activate TAP
3. Run `tap fetch netfilter_isolator`
4. Run `tap build netfilter_isolator`
5. Output is in `nftables/output_rel_x86_64` and `nftables/output_rel_arm64`

## Public build instructions
For libmnl and libnftnl do:
1. cd \<lib dir>
2. touch *
3. rm -rf build
4. mkdir -p build 
5. cd build
6. ../configure --prefix "\<output dir>" LDFLAGS="--static" --disable-shared
7. make
8. make install

Set environment variables to respective outputs:
- export LIBMNL_LIBS=" -L\<output dir>/lib -lmnl "
- export LIBMNL_CFLAGS=" -I\<output dir>/include "
- export LIBNFTNL_LIBS=" -L\<output dir>/lib -lnftnl "
- export LIBNFTNL_CFLAGS=" -I\<output dir>/include "

For nftables follow same build steps as libmnl and libnftnl but after setting the environment variables