import RPi.GPIO as GPIO  
from time import sleep  

in1, in2, en = 23, 24, 25  
GPIO.setmode(GPIO.BCM)  
GPIO.setup([in1, in2, en], GPIO.OUT)  
GPIO.output([in1, in2], GPIO.LOW)  
p = GPIO.PWM(en, 1000)  
p.start(25)  

print("Commands: r-run, s-stop, f-forward, l-low, m-medium, h-high, e-exit")  

try:  
    while True:  
        cmd = input().strip().lower()  
        if cmd == "r":  
            GPIO.output(in1, GPIO.HIGH)  
            GPIO.output(in2, GPIO.LOW)  
        elif cmd == "s":  
            GPIO.output([in1, in2], GPIO.LOW)  
        elif cmd == "f":  
            GPIO.output(in1, GPIO.HIGH)  
            GPIO.output(in2, GPIO.LOW)  
        elif cmd in "lmh":  
            p.ChangeDutyCycle({"l": 25, "m": 50, "h": 75}[cmd])  
        elif cmd == "e":  
            break  
        else:  
            print("Invalid input.")  
except KeyboardInterrupt:  
    print("\nInterrupted!")  
finally:  
    GPIO.cleanup()  
    print("GPIO Clean up done.")
