PROJECT_NAME     := aes_pca10056
TARGETS          := nrf52840_xxaa
OUTPUT_DIRECTORY := _build

SDK_ROOT := ../../../../../../..
PROJ_DIR := ../../..

$(OUTPUT_DIRECTORY)/nrf52840_xxaa.out: \
  LINKER_SCRIPT  := aes_gcc_nrf52.ld

# Source files common to all targets
SRC_FILES += \
  $(SDK_ROOT)/modules/nrfx/mdk/gcc_startup_nrf52840.S \
  $(SDK_ROOT)/components/libraries/log/src/nrf_log_backend_rtt.c \
  $(SDK_ROOT)/components/libraries/log/src/nrf_log_backend_serial.c \
  $(SDK_ROOT)/components/libraries/log/src/nrf_log_backend_uart.c \
  $(SDK_ROOT)/components/libraries/log/src/nrf_log_default_backends.c \
  $(SDK_ROOT)/components/libraries/log/src/nrf_log_frontend.c \
  $(SDK_ROOT)/components/libraries/log/src/nrf_log_str_formatter.c \
  $(SDK_ROOT)/components/boards/boards.c \
  $(SDK_ROOT)/components/libraries/util/app_error.c \
  $(SDK_ROOT)/components/libraries/util/app_error_handler_gcc.c \
  $(SDK_ROOT)/components/libraries/util/app_error_weak.c \
  $(SDK_ROOT)/components/libraries/util/app_util_platform.c \
  $(SDK_ROOT)/components/libraries/util/nrf_assert.c \
  $(SDK_ROOT)/components/libraries/atomic/nrf_atomic.c \
  $(SDK_ROOT)/components/libraries/balloc/nrf_balloc.c \
  $(SDK_ROOT)/external/fprintf/nrf_fprintf.c \
  $(SDK_ROOT)/external/fprintf/nrf_fprintf_format.c \
  $(SDK_ROOT)/components/libraries/memobj/nrf_memobj.c \
  $(SDK_ROOT)/components/libraries/ringbuf/nrf_ringbuf.c \
  $(SDK_ROOT)/components/libraries/strerror/nrf_strerror.c \
  $(SDK_ROOT)/integration/nrfx/legacy/nrf_drv_uart.c \
  $(SDK_ROOT)/modules/nrfx/drivers/src/prs/nrfx_prs.c \
  $(SDK_ROOT)/modules/nrfx/drivers/src/nrfx_uart.c \
  $(SDK_ROOT)/modules/nrfx/drivers/src/nrfx_uarte.c \
  $(PROJ_DIR)/integration_test_ssi_aes_vectors.c \
  $(PROJ_DIR)/main.c \
  $(SDK_ROOT)/external/segger_rtt/SEGGER_RTT.c \
  $(SDK_ROOT)/external/segger_rtt/SEGGER_RTT_Syscalls_GCC.c \
  $(SDK_ROOT)/external/segger_rtt/SEGGER_RTT_printf.c \
  $(SDK_ROOT)/external/nrf_cc310/common/integration_test_plat_utils.c \
  $(SDK_ROOT)/modules/nrfx/mdk/system_nrf52840.c \

# Include folders common to all targets
INC_FOLDERS += \
  $(SDK_ROOT)/external/fprintf \
  $(PROJ_DIR) \
  $(SDK_ROOT)/components/libraries/experimental_section_vars \
  $(SDK_ROOT)/external/nrf_cc310/include \
  $(SDK_ROOT)/components/libraries/atomic \
  $(SDK_ROOT)/components/libraries/delay \
  ../config \
  $(SDK_ROOT)/components/toolchain/cmsis/include \
  $(SDK_ROOT)/components/libraries/balloc \
  $(SDK_ROOT)/components/libraries/log \
  $(SDK_ROOT)/components/libraries/memobj \
  $(SDK_ROOT)/components \
  $(SDK_ROOT)/modules/nrfx/mdk \
  $(SDK_ROOT)/components/libraries/strerror \
  $(SDK_ROOT)/integration/nrfx \
  $(SDK_ROOT)/modules/nrfx/drivers/include \
  $(SDK_ROOT)/components/libraries/ringbuf \
  $(SDK_ROOT)/modules/nrfx \
  $(SDK_ROOT)/components/drivers_nrf/nrf_soc_nosd \
  $(SDK_ROOT)/components/libraries/log/src \
  $(SDK_ROOT)/external/segger_rtt \
  $(SDK_ROOT)/modules/nrfx/hal \
  $(SDK_ROOT)/components/libraries/bsp \
  $(SDK_ROOT)/components/boards \
  $(SDK_ROOT)/integration/nrfx/legacy \
  $(SDK_ROOT)/components/libraries/util \
  $(SDK_ROOT)/external/nrf_cc310/common \

# Libraries common to all targets
LIB_FILES += \
  $(SDK_ROOT)/external/nrf_cc310/lib/libnrf_cc310_0.9.10.a \

# Optimization flags
OPT = -O3 -g3
# Uncomment the line below to enable link time optimization
#OPT += -flto

# C flags common to all targets
CFLAGS += $(OPT)
CFLAGS += -DAES_INTEGTEST
CFLAGS += -DBOARD_PCA10056
CFLAGS += -DBSP_DEFINES_ONLY
CFLAGS += -DCONFIG_GPIO_AS_PINRESET
CFLAGS += -DDEBUG
CFLAGS += -DDEBUG_NRF
CFLAGS += -DDX_CC_TEE
CFLAGS += -DFLOAT_ABI_HARD
CFLAGS += -DNRF52840_XXAA
CFLAGS += -DNRF_SDK_PRESENT
CFLAGS += -mcpu=cortex-m4
CFLAGS += -mthumb -mabi=aapcs
CFLAGS += -Wall -Werror
CFLAGS += -mfloat-abi=hard -mfpu=fpv4-sp-d16
# keep every function in a separate section, this allows linker to discard unused ones
CFLAGS += -ffunction-sections -fdata-sections -fno-strict-aliasing
CFLAGS += -fno-builtin -fshort-enums

# C++ flags common to all targets
CXXFLAGS += $(OPT)

# Assembler flags common to all targets
ASMFLAGS += -g3
ASMFLAGS += -mcpu=cortex-m4
ASMFLAGS += -mthumb -mabi=aapcs
ASMFLAGS += -mfloat-abi=hard -mfpu=fpv4-sp-d16
ASMFLAGS += -DAES_INTEGTEST
ASMFLAGS += -DBOARD_PCA10056
ASMFLAGS += -DBSP_DEFINES_ONLY
ASMFLAGS += -DCONFIG_GPIO_AS_PINRESET
ASMFLAGS += -DDEBUG
ASMFLAGS += -DDEBUG_NRF
ASMFLAGS += -DDX_CC_TEE
ASMFLAGS += -DFLOAT_ABI_HARD
ASMFLAGS += -DNRF52840_XXAA
ASMFLAGS += -DNRF_SDK_PRESENT

# Linker flags
LDFLAGS += $(OPT)
LDFLAGS += -mthumb -mabi=aapcs -L$(SDK_ROOT)/modules/nrfx/mdk -T$(LINKER_SCRIPT)
LDFLAGS += -mcpu=cortex-m4
LDFLAGS += -mfloat-abi=hard -mfpu=fpv4-sp-d16
# let linker dump unused sections
LDFLAGS += -Wl,--gc-sections
# use newlib in nano version
LDFLAGS += --specs=nano.specs

nrf52840_xxaa: CFLAGS += -D__HEAP_SIZE=0
nrf52840_xxaa: CFLAGS += -D__STACK_SIZE=16384
nrf52840_xxaa: ASMFLAGS += -D__HEAP_SIZE=0
nrf52840_xxaa: ASMFLAGS += -D__STACK_SIZE=16384

# Add standard libraries at the very end of the linker input, after all objects
# that may need symbols provided by these libraries.
LIB_FILES += -lc -lnosys -lm

## ----------------------------------------------------------------------------- ##
## wolfSSL source files##
## ----------------------------------------------------------------------------- ##

# config #1 works

# AES only

# SRC_FILES += \
#   $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/sha256.c \
#   $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/aes.c \
#   $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/wc_encrypt.c \
#   $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/tfm.c \

# config #2 works

SRC_FILES += \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/random.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/aes.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/selftest.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/wolfmath.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/chacha20_poly1305.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/cpuid.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/sp_arm32.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/sp_c32.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/pkcs12.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/wolfevent.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/chacha.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/ge_low_mem.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/des3.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/sp_c64.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/pkcs7.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/dsa.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/wc_pkcs11.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/asm.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/sp_cortexm.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/integer.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/md4.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/wc_encrypt.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/sha3.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/pwdbased.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/ecc_fp.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/poly1305.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/hc128.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/hmac.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/cmac.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/rsa.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/asn.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/wolfcrypt_first.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/cryptocb.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/sp_arm64.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/random.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/idea.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/dh.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/ed25519.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/wc_port.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/hash.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/rabbit.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/arc4.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/md5.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/signature.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/fe_low_mem.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/ripemd.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/error.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/sha512.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/srp.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/curve25519.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/ge_operations.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/aes.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/wolfcrypt_last.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/sp_int.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/logging.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/fe_operations.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/coding.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/blake2b.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/port/arm/armv8-sha256.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/port/arm/armv8-aes.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/fips_test.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/md2.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/sha.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/async.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/compress.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/ecc.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/camellia.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/fips.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/sp_armthumb.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/tfm.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/sp_x86_64.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/memory.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/sha256.c \

  # $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/sha256_cert.c \ multiple definition build error from test.c
  # $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/evp.c \ doesn't need to be comp
  # $(SDK_ROOT)/external/wolfssl/wolfcrypt/src/misc.c \

# Test source code

  SRC_FILES += \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/test/test_aes.c \
  $(SDK_ROOT)/external/wolfssl/wolfcrypt/benchmark/benchmark.c \


  # $(SDK_ROOT)/external/wolfssl/wolfcrypt/benchmark/benchmark.c \

INC_FOLDERS += \
  . \
  $(SDK_ROOT)/external/wolfssl \

#wolfSSL preprocessor to use user_settings.h
CFLAGS += -DWOLFSSL_USER_SETTINGS

## ----------------------------------------------------------------------------- ##


.PHONY: default help

# Default target - first one defined
default: nrf52840_xxaa

# Print all targets that can be built
help:
	@echo following targets are available:
	@echo		nrf52840_xxaa
	@echo		sdk_config - starting external tool for editing sdk_config.h
	@echo		flash      - flashing binary

TEMPLATE_PATH := $(SDK_ROOT)/components/toolchain/gcc


include $(TEMPLATE_PATH)/Makefile.common

$(foreach target, $(TARGETS), $(call define_target, $(target)))

.PHONY: flash erase

# Flash the program
flash: default
	@echo Flashing: $(OUTPUT_DIRECTORY)/nrf52840_xxaa.hex
	nrfjprog -f nrf52 --program $(OUTPUT_DIRECTORY)/nrf52840_xxaa.hex --sectorerase
	nrfjprog -f nrf52 --reset

erase:
	nrfjprog -f nrf52 --eraseall

SDK_CONFIG_FILE := ../config/sdk_config.h
CMSIS_CONFIG_TOOL := $(SDK_ROOT)/external_tools/cmsisconfig/CMSIS_Configuration_Wizard.jar
sdk_config:
	java -jar $(CMSIS_CONFIG_TOOL) $(SDK_CONFIG_FILE)
