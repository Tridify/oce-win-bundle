###### FreeType
PROJECT(freetype)
INCLUDE_DIRECTORIES(${FT_DIR}/include)
INCLUDE_DIRECTORIES(${FT_DIR})
ADD_DEFINITIONS(-DFT2_BUILD_LIBRARY)
ADD_DEFINITIONS(-D_CRT_SECURE_NO_WARNINGS)

SET ( FT_SOURCE_FILES
    ${FT_DIR}/src/autofit/autofit.c
    ${FT_DIR}/src/bdf/bdf.c
    ${FT_DIR}/src/cff/cff.c
    ${FT_DIR}/src/base/ftbase.c
    ${FT_DIR}/src/base/ftbitmap.c
    ${FT_DIR}/src/cache/ftcache.c
    ${FT_DIR}/src/base/ftdebug.c
    ${FT_DIR}/src/base/ftfstype.c
    ${FT_DIR}/src/base/ftgasp.c
    ${FT_DIR}/src/base/ftglyph.c
    ${FT_DIR}/src/gzip/ftgzip.c
    ${FT_DIR}/src/base/ftinit.c
    ${FT_DIR}/src/lzw/ftlzw.c
    ${FT_DIR}/src/base/ftstroke.c
    ${FT_DIR}/src/base/ftsystem.c
    ${FT_DIR}/src/smooth/smooth.c
    )
    
IF(MSVC)
     LIST (APPEND FT_SOURCE_FILES freetype.def)
ENDIF()
    
SET ( FT_MODULES 
    ${FT_DIR}/src/base/ftbbox.c
    ${FT_DIR}/src/base/ftgxval.c
    ${FT_DIR}/src/base/ftlcdfil.c
    ${FT_DIR}/src/base/ftmm.c
    ${FT_DIR}/src/base/ftotval.c
    ${FT_DIR}/src/base/ftpatent.c
    ${FT_DIR}/src/base/ftpfr.c
    ${FT_DIR}/src/base/ftsynth.c
    ${FT_DIR}/src/base/fttype1.c
    ${FT_DIR}/src/base/ftwinfnt.c
    ${FT_DIR}/src/base/ftxf86.c
    ${FT_DIR}/src/pcf/pcf.c
    ${FT_DIR}/src/pfr/pfr.c
    ${FT_DIR}/src/psaux/psaux.c
    ${FT_DIR}/src/pshinter/pshinter.c
    ${FT_DIR}/src/psnames/psmodule.c
    ${FT_DIR}/src/raster/raster.c
    ${FT_DIR}/src/sfnt/sfnt.c
    ${FT_DIR}/src/truetype/truetype.c
    ${FT_DIR}/src/type1/type1.c
    ${FT_DIR}/src/cid/type1cid.c
    ${FT_DIR}/src/type42/type42.c
    ${FT_DIR}/src/winfonts/winfnt.c
    )

ADD_LIBRARY(freetype ${BUNDLE_LIB_MODIFIER} ${FT_SOURCE_FILES} ${FT_MODULES} )  

INSTALL(DIRECTORY ${FT_DIR}/include/
    DESTINATION ${OCE_WIN_BUNDLE_INSTALL_DIR}/include/freetype
    PATTERN "internal" EXCLUDE
    )

INSTALL(TARGETS freetype
    ARCHIVE DESTINATION  "${OCE_WIN_BUNDLE_INSTALL_DIR_BITS}/lib/" CONFIGURATIONS Debug Release MinSizeRel RelWithDebInfo
    LIBRARY DESTINATION  "${OCE_WIN_BUNDLE_INSTALL_DIR_BITS}/lib/" CONFIGURATIONS Debug Release MinSizeRel RelWithDebInfo
    RUNTIME DESTINATION  "${OCE_WIN_BUNDLE_INSTALL_DIR_BITS}/bin/" CONFIGURATIONS Debug Release MinSizeRel RelWithDebInfo
    )
