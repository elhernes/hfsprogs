# newfs_hfs - Create HFS filesystems

set(NEWFS_HFS_SOURCES
    hfs_endian.c
    makehfs.c
    newfs_hfs.c
)

add_executable(newfs_hfs ${NEWFS_HFS_SOURCES})

# Find OpenSSL for crypto library
find_package(OpenSSL REQUIRED)
target_link_libraries(newfs_hfs PRIVATE OpenSSL::Crypto)

# Installation
install(TARGETS newfs_hfs
    RUNTIME DESTINATION ${CMAKE_INSTALL_SBINDIR}
)

# Create mkfs.hfsplus symlink
install(CODE "execute_process(COMMAND ${CMAKE_COMMAND} -E create_symlink newfs_hfs \$ENV{DESTDIR}\${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_SBINDIR}/mkfs.hfsplus)")

install(FILES newfs_hfs.8
    DESTINATION ${CMAKE_INSTALL_MANDIR}/man8
)

# Install boot data file
install(FILES hfsbootdata.img
    DESTINATION ${CMAKE_INSTALL_DATADIR}/misc
    RENAME hfsbootdata
    PERMISSIONS OWNER_READ GROUP_READ WORLD_READ
)
