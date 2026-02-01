# dfalib - HFS filesystem repair library

set(DFALIB_SOURCES
    hfs_endian.c
    BlockCache.c
    BTree.c
    BTreeAllocate.c
    BTreeMiscOps.c
    BTreeNodeOps.c
    BTreeScanner.c
    BTreeTreeOps.c
    CatalogCheck.c
    HardLinkCheck.c
    SBTree.c
    SControl.c
    SVerify1.c
    SVerify2.c
    SRepair.c
    SRebuildCatalogBTree.c
    SUtils.c
    SKeyCompare.c
    SDevice.c
    SExtents.c
    SAllocate.c
    SCatalog.c
    SStubs.c
    VolumeBitmapCheck.c
)

add_library(dfa STATIC ${DFALIB_SOURCES})

# Include the project's main include directory
target_include_directories(dfa PUBLIC
    ${CMAKE_SOURCE_DIR}/include
    ${CMAKE_CURRENT_SOURCE_DIR}
)
