#############################################################################MAN

include( Gzip )

set( QUCS_URL       "https://sf.net/p/qucs" )
set( QUCS_BUGREPORT "qucs-bugs@lists.sourceforge.net" )

configure_file(
	"${CMAKE_SOURCE_DIR}/doc/qucsrflayout.1.in"
	"${CMAKE_BINARY_DIR}/doc/qucsrflayout.1"
	@ONLY
	)

compress_gz( -9
	"${CMAKE_BINARY_DIR}/doc/qucsrflayout.1"
	"${CMAKE_BINARY_DIR}/doc/qucsrflayout.1.gz"
	)

install(
	FILES "${CMAKE_BINARY_DIR}/doc/qucsrflayout.1.gz"
	CONFIGURATIONS Release
	DESTINATION "share/man/man1" #"${CMAKE_INSTALL_MANDIR}"
	)

compress_gz( -9
	"${CMAKE_SOURCE_DIR}/CHANGELOG"
	"${CMAKE_BINARY_DIR}/doc/changelog.gz"
	)

install(
	FILES "${CMAKE_BINARY_DIR}/doc/changelog.gz"
	CONFIGURATIONS Release
	DESTINATION "share/doc/qucsrflayout" #"${CMAKE_INSTALL_MANDIR}"
	)

###########################################################################LATEX

add_subdirectory( "${CMAKE_CURRENT_SOURCE_DIR}/latex" )
