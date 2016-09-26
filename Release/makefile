################################################################################
# Automatically-generated file. Do not edit!
################################################################################

-include ../makefile.init

RM := rm -rf

# All of the sources participating in the build are defined here
-include sources.mk
-include subdir.mk
-include objects.mk

ifneq ($(MAKECMDGOALS),clean)
ifneq ($(strip $(ASM_DEPS)),)
-include $(ASM_DEPS)
endif
ifneq ($(strip $(S_DEPS)),)
-include $(S_DEPS)
endif
ifneq ($(strip $(S_UPPER_DEPS)),)
-include $(S_UPPER_DEPS)
endif
ifneq ($(strip $(C_DEPS)),)
-include $(C_DEPS)
endif
endif

-include ../makefile.defs

# Add inputs and outputs from these tool invocations to the build variables 
LSS += \
ThreeLED.lss \

FLASH_IMAGE += \
ThreeLED.hex \

EEPROM_IMAGE += \
ThreeLED.eep \

SIZEDUMMY += \
sizedummy \


# All Target
all: ThreeLED.elf secondary-outputs

# Tool invocations
ThreeLED.elf: $(OBJS) $(USER_OBJS)
	@echo 'Building target: $@'
	@echo 'Invoking: AVR C Linker'
	avr-gcc -Wl,-Map,ThreeLED.map -mmcu=atmega328p -o "ThreeLED.elf" $(OBJS) $(USER_OBJS) $(LIBS)
	@echo 'Finished building target: $@'
	@echo ' '

ThreeLED.lss: ThreeLED.elf
	@echo 'Invoking: AVR Create Extended Listing'
	-avr-objdump -h -S ThreeLED.elf  >"ThreeLED.lss"
	@echo 'Finished building: $@'
	@echo ' '

ThreeLED.hex: ThreeLED.elf
	@echo 'Create Flash image (ihex format)'
	-avr-objcopy -R .eeprom -R .fuse -R .lock -R .signature -O ihex ThreeLED.elf  "ThreeLED.hex"
	@echo 'Finished building: $@'
	@echo ' '

ThreeLED.eep: ThreeLED.elf
	@echo 'Create eeprom image (ihex format)'
	-avr-objcopy -j .eeprom --no-change-warnings --change-section-lma .eeprom=0 -O ihex ThreeLED.elf  "ThreeLED.eep"
	@echo 'Finished building: $@'
	@echo ' '

sizedummy: ThreeLED.elf
	@echo 'Invoking: Print Size'
	-avr-size --format=avr --mcu=atmega328p ThreeLED.elf
	@echo 'Finished building: $@'
	@echo ' '

# Other Targets
clean:
	-$(RM) $(FLASH_IMAGE)$(ELFS)$(OBJS)$(ASM_DEPS)$(EEPROM_IMAGE)$(S_DEPS)$(SIZEDUMMY)$(S_UPPER_DEPS)$(LSS)$(C_DEPS) ThreeLED.elf
	-@echo ' '

secondary-outputs: $(LSS) $(FLASH_IMAGE) $(EEPROM_IMAGE) $(SIZEDUMMY)

.PHONY: all clean dependents
.SECONDARY:

-include ../makefile.targets
