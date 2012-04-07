# tests
# based on Makefile.in.

set ( SRC_TESTS
	teststrmatch.c testuri.c testuuid.c testbuckets.c testpass.c
	testmd4.c testmd5.c testldap.c testdate.c testdbm.c testdbd.c
	testxml.c testrmm.c testreslist.c testqueue.c testxlate.c
	testmemcache.c testcrypto.c
)

add_executable ( testall abts.c testutil.c ${SRC_TESTS} ${_extra_libs} )
target_link_libraries ( testall ${APR_UTIL_LIBS} ${APR_LIBRARIES} ${EXPAT_LIBRARY} ${CRYPT_LIB} )

add_executable ( dbd dbd.c ${_extra_libs} )
target_link_libraries ( dbd ${APR_UTIL_LIBS} ${APR_LIBRARIES} )

add_test ( testall testall )
add_test ( dbd dbd )
