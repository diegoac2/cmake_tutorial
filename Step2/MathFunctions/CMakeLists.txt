# TODO 14: Remove mysqrt.cxx from the list of sources

# Add a library called MathFunctions with sources MathFunctions.cxx
# and mysqrt.cxx
# Hint: You will need the add_library command
add_library(MathFunctions MathFunctions.cxx)
# Create a variable USE_MYMATH using option and set default to ON
option(USE_MYMATH "Use tutorial provided math implementation" ON)

# If USE_MYMATH is ON, use target_compile_definitions to pass
# USE_MYMATH as a precompiled definition to our source files
if (USE_MYMATH)
  target_compile_definitions(MathFunctions PRIVATE "USE_MYMATH")
  # When USE_MYMATH is ON, add a library for SqrtLibrary with
  # source mysqrt.cxx
  add_library(SqrtLibrary STATIC mysqrt.cxx)
  # When USE_MYMATH is ON, link SqrtLibrary to the MathFunctions Library
  target_link_libraries(MathFunctions PRIVATE SqrtLibrary)
endif()



