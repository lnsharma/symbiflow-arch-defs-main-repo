add_file_target(FILE counter.v SCANNER_TYPE verilog)
add_file_target(FILE test.pcf)

add_fpga_target(
  NAME counter-umc22-no-adder
  BOARD qlf_k4n8-qlf_k4n8_umc22_board
  SOURCES counter.v
  INPUT_IO_FILE test.pcf
  EXPLICIT_ADD_FILE_TARGET
  DEFINES SYNTH_OPTS=-no_adder
)

add_fpga_target(
  NAME counter-umc22-adder
  BOARD qlf_k4n8-qlf_k4n8_umc22_board
  SOURCES counter.v
  INPUT_IO_FILE test.pcf
  EXPLICIT_ADD_FILE_TARGET
  )

add_dependencies(all_qlf_k4n8_tests_no_adder counter-umc22-no-adder_route)
add_dependencies(all_qlf_k4n8_tests_adder    counter-umc22-adder_route)
