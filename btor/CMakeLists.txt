add_library(smt-switch-btor SHARED
  "${CMAKE_CURRENT_SOURCE_DIR}/src/boolector_extensions.cpp"
  "${CMAKE_CURRENT_SOURCE_DIR}/src/boolector_factory.cpp"
  "${CMAKE_CURRENT_SOURCE_DIR}/src/boolector_fun.cpp"
  "${CMAKE_CURRENT_SOURCE_DIR}/src/boolector_solver.cpp"
  "${CMAKE_CURRENT_SOURCE_DIR}/src/boolector_sort.cpp"
  "${CMAKE_CURRENT_SOURCE_DIR}/src/boolector_term.cpp"
  "${BTOR_HOME}/deps/btor2tools/build/btor2parser.o"
  )
target_include_directories (smt-switch-btor PUBLIC "${PROJECT_SOURCE_DIR}/include")
target_include_directories (smt-switch-btor PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/include")
target_include_directories (smt-switch-btor PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/btor/include")
target_include_directories (smt-switch-btor PUBLIC "${BTOR_HOME}/src")

target_link_libraries(smt-switch-btor "${BTOR_HOME}/build/lib/libboolector.a")
target_link_libraries(smt-switch-btor "${BTOR_HOME}/deps/lingeling/liblgl.a")
target_link_libraries(smt-switch-btor smt-switch)
target_link_libraries(smt-switch-btor pthread)
target_link_libraries(smt-switch-btor m)

install(TARGETS smt-switch-btor DESTINATION lib)