add_library(MathFunctions mysqrt.cxx)
#########################################################
#CMD3
#########################################################
install(TARGETS MathFunctions DESTINATION bin)
install(FILES mysqrt.h DESTINATION include)