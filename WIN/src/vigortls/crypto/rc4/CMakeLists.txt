include_directories(${CMAKE_CURRENT_BINARY_DIR} .. ../../include . ../evp)

if (${ARCH} STREQUAL "x86_64")
    set(
        RC4_ARCH_SOURCES

        rc4-x86_64.${ASM_EXT}
    )
elseif (${ARCH} STREQUAL "x86")
    set(
        RC4_ARCH_SOURCES

        rc4-586.${ASM_EXT}
    )
endif()

add_library(
    rc4

    OBJECT

    rc4.c
    ${RC4_ARCH_SOURCES}
)

perlasm(rc4-x86_64.${ASM_EXT} asm/rc4-x86_64.pl)
perlasm(rc4-586.${ASM_EXT} asm/rc4-586.pl)
