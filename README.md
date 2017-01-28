Shift Register 74HC595
=======

Dynamic class to manage Shift Register 74HC595 with C.H.I.P. using Python

#Requirements

    * Next Thing Co. C.H.I.P.
    * Python 2.6+
    * CHIP_IO (latest version recommended)

#Installation

    Install CHIP_IO library:

        https://github.com/xtacocorex/CHIP_IO.git

    Get this library:

        # git clone git@github.com:Ithaca1937/shiftr_74HC595.git


#Example

      import CHIP_IO.GPIO as GPIO
      from shiftr_74HC595 import ShiftRegister
      from time import sleep

      data_pin = "GPIO1" #pin 14 on the 74HC595
      latch_pin = "GPIO2" #pin 12 on the 74HC595
      clock_pin = "GPIO3" #pin 11 on the 74HC595
      shift_register = ShiftRegister(data_pin, latch_pin, clock_pin)

      try:
          while 1:
              shift_register.setOutput(0, GPIO.LOW)
              shift_register.setOutput(1, GPIO.LOW)
              shift_register.setOutput(2, GPIO.LOW)
              shift_register.setOutput(3, GPIO.HIGH)
              shift_register.setOutput(4, GPIO.LOW)
              shift_register.setOutput(5, GPIO.LOW)
              shift_register.setOutput(6, GPIO.HIGH)
              shift_register.setOutput(7, GPIO.HIGH)
              sleep(1)

              shift_register.setOutput(0, GPIO.LOW)
              shift_register.setOutput(1, GPIO.LOW)
              shift_register.setOutput(2, GPIO.HIGH)
              shift_register.setOutput(3, GPIO.LOW)
              shift_register.setOutput(4, GPIO.LOW)
              shift_register.setOutput(5, GPIO.HIGH)
              shift_register.setOutput(6, GPIO.LOW)
              shift_register.setOutput(7, GPIO.HIGH)
              sleep(1)
      except KeyboardInterrupt:
          print
          print "Ctrl-C quit"
      finally:
          shift_register.setOutput(0, GPIO.LOW)
          shift_register.setOutput(1, GPIO.LOW)
          shift_register.setOutput(2, GPIO.LOW)
          shift_register.setOutput(3, GPIO.LOW)
          shift_register.setOutput(4, GPIO.LOW)
          shift_register.setOutput(5, GPIO.LOW)
          shift_register.setOutput(6, GPIO.LOW)
          shift_register.setOutput(7, GPIO.LOW)
          GPIO.cleanup()
