# fsck_hfs - HFS filesystem checker

# Build the dfalib static library first
add_subdirectory(dfalib)

set(FSCK_HFS_SOURCES
    fsck_hfs.c
    strings.c
    utilities.c
    cache.c
    fsck_debug.c
)

add_executable(fsck_hfs ${FSCK_HFS_SOURCES})

# Include dfalib headers
target_include_directories(fsck_hfs PRIVATE dfalib)

# Link against dfalib and libbsd
target_link_libraries(fsck_hfs PRIVATE dfa)

find_library(BSD_LIBRARY bsd REQUIRED)
target_link_libraries(fsck_hfs PRIVATE ${BSD_LIBRARY})

# Installation
install(TARGETS fsck_hfs
    RUNTIME DESTINATION ${CMAKE_INSTALL_SBINDIR}
)

install(FILES fsck_hfs.8
    DESTINATION ${CMAKE_INSTALL_MANDIR}/man8
)
