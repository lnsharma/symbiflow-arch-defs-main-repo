add_file_target(FILE adder_8.v SCANNER_TYPE verilog)
add_file_target(FILE adder_8.pcf)

add_fpga_target(
  NAME adder_8-umc22-no-adder
  BOARD qlf_k4n8-qlf_k4n8_umc22_board
  SOURCES adder_8.v
  INPUT_IO_FILE adder_8.pcf
  EXPLICIT_ADD_FILE_TARGET
  DEFINES SYNTH_OPTS=-no_adder
)

add_fpga_target(
  NAME adder_8-umc22-adder
  BOARD qlf_k4n8-qlf_k4n8_umc22_board
  SOURCES adder_8.v
  INPUT_IO_FILE adder_8.pcf
  EXPLICIT_ADD_FILE_TARGET
  )

add_dependencies(all_qlf_k4n8_tests_no_adder adder_8-umc22-no-adder_route)
add_dependencies(all_qlf_k4n8_tests_adder    adder_8-umc22-adder_route)
