# lmdb/test/CMakeLists.txt

message("Configuring tests...")

#For detecting double-free():
#add_definitions(-DPRINT_MALLOC)

include_directories("${CMAKE_CURRENT_SOURCE_DIR}/../source")

add_executable(mdb_copy ../liblmdb/mdb_copy.c)
target_link_libraries(mdb_copy liblmdb)
add_executable(mdb_dump ../liblmdb/mdb_dump.c)
target_link_libraries(mdb_dump liblmdb)
add_executable(mdb_load ../liblmdb/mdb_load.c)
target_link_libraries(mdb_load liblmdb)
add_executable(mdb_stat ../liblmdb/mdb_stat.c)
target_link_libraries(mdb_stat liblmdb)
add_executable(mtest ../liblmdb/mtest.c)
target_link_libraries(mtest liblmdb)
add_executable(mtest2 ../liblmdb/mtest2.c)
target_link_libraries(mtest2 liblmdb)
add_executable(mtest3 ../liblmdb/mtest3.c)
target_link_libraries(mtest3 liblmdb)
add_executable(mtest4 ../liblmdb/mtest4.c)
target_link_libraries(mtest4 liblmdb)
add_executable(mtest5 ../liblmdb/mtest5.c)
target_link_libraries(mtest5 liblmdb)
add_executable(mtest6 ../liblmdb/mtest6.c)
target_link_libraries(mtest6 liblmdb)
