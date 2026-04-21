# Adding post build command to get a dll and its pdb to the current bin  directory
Example using zLib
```
set(ZLIB_INSTALLED_DIR "C:\\Libs\\zLib")
list(APPEND CMAKE_PREFIX_PATH "${ZLIB_INSTALLED_DIR}\\${ZLIB_SUB_FOLDER}")
#list(APPEND CMAKE_PREFIX_PATH "${ZLIB_INSTALLED_DIR}\\")
#find_package(zlib)
# import targets   ZLIB::ZLIB and ZLIB::ZLIBSTATIC
find_package(ZLIB CONFIG COMPONENTS shared static REQUIRED)

#print_target_properties (ZLIB::ZLIB)
get_target_property(ZLIB_DLL ZLIB::ZLIB LOCATION)
string(REPLACE ".dll" ".pdb" ZLIB_PDB ${ZLIB_DLL})

message ("####### ZLIB dll = ${ZLIB_DLL}")
message ("####### ZLIB pdb = ${ZLIB_PDB}")
```
Now you can add these post build commands :
```
add_custom_command(
    TARGET ${my_target} POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_if_different
        $<TARGET_RUNTIME_DLLS:${my_target}> $<TARGET_FILE_DIR:${my_target}>
    COMMAND_EXPAND_LISTS
)
add_custom_command(
   TARGET ${my_target} POST_BUILD
   COMMAND ${CMAKE_COMMAND} -E copy_if_different
       ${ZLIB_PDB} $<TARGET_FILE_DIR:${my_target}>
   COMMAND_EXPAND_LISTS
)
```
The second command is needed to copy the pdb file.
It's a pitty cmake does not (yet) handle this by itself !
