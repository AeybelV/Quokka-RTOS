# ========== QUOKKA KERNEL ==========

set(SOURCES
  kernel.c
  )
add_executable(quokka_kernel ${SOURCES})


# Add pico_stdlib library which aggregates commonly used features
target_link_libraries(quokka_kernel pico_stdlib)

# create map/bin/hex/uf2 file in addition to ELF.
pico_add_extra_outputs(quokka_kernel)
