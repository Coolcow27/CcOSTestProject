 
set ( CURRENT_PROJECT CcOSExampleProject )

########
# Add Source Files
########
file (GLOB SOURCE_FILES
      "src/*.c"
      "src/*.cpp"
      "*.h")
      

include_directories( ${CMAKE_CURRENT_SOURCE_DIR} )
                     
if(WINDOWS)
  CcOSExampleProjectGenerateRcFileToCurrentDir(${CURRENT_PROJECT} SOURCE_FILES)
endif()

add_executable( ${CURRENT_PROJECT} ${SOURCE_FILES} )

# To keep Header an Source together, display them in same Directory
# It will only work with IDE's wich are supporting this features
SOURCE_GROUP( ""        FILES ${SOURCE_FILES})

target_link_libraries ( ${CURRENT_PROJECT} LINK_PUBLIC
                              CcKernel  )

#################
# Post configuration steps
#################
CcOSExampleProjectTargetIncludeDirs( ${CURRENT_PROJECT} ${CMAKE_CURRENT_SOURCE_DIR})
CcOSExampleProjectLibSettings(${CURRENT_PROJECT} TRUE TRUE ${SOURCE_FILES})
