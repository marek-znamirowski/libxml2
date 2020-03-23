cmake_minimum_required(VERSION 2.8)
project (libxml2)

set (PROJECT_SOURCES
  ${CMAKE_CURRENT_SOURCE_DIR}/buf					 
  ${CMAKE_CURRENT_SOURCE_DIR}/c14n				 
  ${CMAKE_CURRENT_SOURCE_DIR}/catalog				 
  ${CMAKE_CURRENT_SOURCE_DIR}/chvalid				 
  ${CMAKE_CURRENT_SOURCE_DIR}/debugXML			 
  ${CMAKE_CURRENT_SOURCE_DIR}/dict				 
  ${CMAKE_CURRENT_SOURCE_DIR}/DOCBparser			 
  ${CMAKE_CURRENT_SOURCE_DIR}/encoding			 
  ${CMAKE_CURRENT_SOURCE_DIR}/entities			 
  ${CMAKE_CURRENT_SOURCE_DIR}/error				 
  ${CMAKE_CURRENT_SOURCE_DIR}/globals				 
  ${CMAKE_CURRENT_SOURCE_DIR}/hash				 
  ${CMAKE_CURRENT_SOURCE_DIR}/HTMLparser			 
  ${CMAKE_CURRENT_SOURCE_DIR}/HTMLtree			 
  ${CMAKE_CURRENT_SOURCE_DIR}/legacy				 
  ${CMAKE_CURRENT_SOURCE_DIR}/list				 
  ${CMAKE_CURRENT_SOURCE_DIR}/nanoftp				 
  ${CMAKE_CURRENT_SOURCE_DIR}/nanohttp			 
  ${CMAKE_CURRENT_SOURCE_DIR}/parser				 
  ${CMAKE_CURRENT_SOURCE_DIR}/parserInternals		 
  ${CMAKE_CURRENT_SOURCE_DIR}/pattern				 
  ${CMAKE_CURRENT_SOURCE_DIR}/relaxng				 
  ${CMAKE_CURRENT_SOURCE_DIR}/SAX2				 
  ${CMAKE_CURRENT_SOURCE_DIR}/SAX					 
  ${CMAKE_CURRENT_SOURCE_DIR}/schematron			 
  ${CMAKE_CURRENT_SOURCE_DIR}/threads				 
  ${CMAKE_CURRENT_SOURCE_DIR}/tree				 
  ${CMAKE_CURRENT_SOURCE_DIR}/uri					 
  ${CMAKE_CURRENT_SOURCE_DIR}/valid				 
  ${CMAKE_CURRENT_SOURCE_DIR}/xinclude			 
  ${CMAKE_CURRENT_SOURCE_DIR}/xlink				 
  ${CMAKE_CURRENT_SOURCE_DIR}/xmlIO				 
  ${CMAKE_CURRENT_SOURCE_DIR}/xmlmemory			 
  ${CMAKE_CURRENT_SOURCE_DIR}/xmlreader			 
  ${CMAKE_CURRENT_SOURCE_DIR}/xmlregexp			 
  ${CMAKE_CURRENT_SOURCE_DIR}/xmlmodule			 
  ${CMAKE_CURRENT_SOURCE_DIR}/xmlsave				 
  ${CMAKE_CURRENT_SOURCE_DIR}/xmlschemas			 
  ${CMAKE_CURRENT_SOURCE_DIR}/xmlschemastypes		 
  ${CMAKE_CURRENT_SOURCE_DIR}/xmlunicode			 
  ${CMAKE_CURRENT_SOURCE_DIR}/xmlwriter			 
  ${CMAKE_CURRENT_SOURCE_DIR}/xpath				 
  ${CMAKE_CURRENT_SOURCE_DIR}/xpointer			 
  ${CMAKE_CURRENT_SOURCE_DIR}/xmlstring            
  )

set(LIBXML2_INCLUDES ${CMAKE_CURRENT_SOURCE_DIR}/include
  CACHE INTERNAL "${PROJECT_NAME}: Include Directories" FORCE)

file(GLOB_RECURSE PROJECT_HEADERS ${CMAKE_CURRENT_SOURCE_DIR}/include/*.h)

source_group("Headers" FILES ${PROJECT_HEADERS})

set (PROJECT_HEADERS)

file(GLOB_RECURSE PROJECT_HEADERS ${CMAKE_CURRENT_SOURCE_DIR}/include/*.h)

add_library(${PROJECT_NAME} STATIC ${PROJECT_SOURCES} ${PROJECT_HEADERS})

target_include_directories(${PROJECT_NAME} PUBLIC $<INSTALL_INTERFACE:include/libxml2>)

foreach(include_dir IN LISTS LIBXML2_INCLUDES)
    target_include_directories(${PROJECT_NAME} PUBLIC $<BUILD_INTERFACE:${include_dir}>)
endforeach()
