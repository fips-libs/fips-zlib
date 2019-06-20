#
# minimal zlib for oryol
#
fips_begin_lib(zlib)
    fips_files(
        adler32.c
        compress.c
        crc32.c crc32.h
        deflate.c deflate.h
        infback.c 
        inffast.c inffast.h
        inffixed.h
        inflate.c inflate.h
        inftrees.c inftrees.h
        trees.c trees.h
        uncompr.c
        zconf.h
        zlib.h
        zutil.c zutil.h
    )

    add_definitions(-DZ_SOLO)

fips_end_lib(zlib)
if (FIPS_CLANG)
    set_target_properties(zlib PROPERTIES COMPILE_FLAGS "-Wno-shift-negative-value")
elseif(FIPS_GCC)
    set_target_properties(zlib PROPERTIES COMPILE_FLAGS "-Wno-implicit-fallthrough")
endif()
