# SNAKE-BOT
import cv2 
import time 
import RPi.GPIO as GPIO 
key = cv2. waitKey(1) 
webcam = cv2.VideoCapture(0) 
GPIO.setmode(GPIO.BOARD) 
Motor11 = 33 # Input1 Pin1 
Motor12 = 31 # Input1 Pin2 
Motor21 = 35 # Input2 Pin1 
Motor22 = 37 # Input2 Pin2 
IRleft = 16 # Left IR sensor 
IRright = 18 # Right IR sensor 
GPIO.setup(Motor11,GPIO.OUT) 
GPIO.setup(Motor12,GPIO.OUT) 
GPIO.setup(Motor21,GPIO.OUT) 
GPIO.setup(Motor22,GPIO.OUT) 
GPIO.setup(IRleft,GPIO.IN) 
GPIO.setup(IRright,GPIO.IN) 
while True: 
 check, frame = webcam.read() 
 #print(check) #prints true as long as the webcam is runningq  #frame = cv2.rotate(frame, cv2.cv2.ROTATE_180_CLOCKWISE)  #print(frame) #prints matrix values of each framecd
 (h, w) = frame.shape[:2] 
 center=(w/2, h/2) 
 c=cv2.getRotationMatrix2D(center, 180, 1.0)  frame=cv2.warpAffine(frame, c, (w,h)) 
 cv2.imshow("Capturing", frame) 
 key = cv2.waitKey(1) 
 time.sleep(0.01) 
 #print(key) 
 x=GPIO.input(IRleft) 
 y=GPIO.input(IRright) 
 #print(x) 
 #print(y) 
 if key == ord('q'): 
 print("Turning off camera.") 
 webcam.release() 
 print("Camera off.") 
 print("Program ended.") 
 print("STOP") 
 GPIO.output(Motor11,GPIO.LOW)  GPIO.output(Motor12,GPIO.LOW)  GPIO.output(Motor21,GPIO.LOW)  GPIO.output(Motor22,GPIO.LOW)  cv2.destroyAllWindows() 
 break 
 elif key == ord('s'): 
 print('image saved')
 cv2.imwrite('image.jpg',frame) 
 elif (key==82 and key!=81 and key!=83 and key!=84):  if (x==1 and y==1): 
 print("UP") 
 GPIO.output(Motor11,GPIO.LOW) 
 GPIO.output(Motor12,GPIO.HIGH) 
 GPIO.output(Motor21,GPIO.LOW) 
 GPIO.output(Motor22,GPIO.HIGH) 
 time.sleep(0.5) 
 elif ((key==81 and key!=82 and key!=83 and key!=84)):  if (x==1): 
 print("LEFT") 
 GPIO.output(Motor11,GPIO.LOW) 
 GPIO.output(Motor12,GPIO.HIGH) 
 GPIO.output(Motor21,GPIO.LOW) 
 GPIO.output(Motor22,GPIO.LOW) 
 time.sleep(0.5) 
 elif key==84 and key!=81 and key!=83 and key!=82:  print("DOWN") 
 GPIO.output(Motor11,GPIO.HIGH) 
 GPIO.output(Motor12,GPIO.LOW) 
 GPIO.output(Motor21,GPIO.HIGH) 
 GPIO.output(Motor22,GPIO.LOW) 
 time.sleep(0.5) 
 elif (key==83 and key!=81 and key!=82 and key!=84):  if (y==1):
 print("RIGHT") 
 GPIO.output(Motor11,GPIO.LOW)  GPIO.output(Motor12,GPIO.LOW)  GPIO.output(Motor21,GPIO.LOW)  GPIO.output(Motor22,GPIO.HIGH)  time.sleep(0.5) 
 else: 
 #elif key == ord('s'): 
 print("STOP") 
 GPIO.output(Motor11,GPIO.LOW)  GPIO.output(Motor12,GPIO.LOW)  GPIO.output(Motor21,GPIO.LOW)  GPIO.output(Motor22,GPIO.LOW) import cv2 
import time 
key = cv2. waitKey(1) 
webcam = cv2.VideoCapture(0) while True: 
 check, frame = webcam.read()  cv2.imshow("Capturing", frame)  key = cv2.waitKey(1) 
 time.sleep(0.01) 
 print(key) 
 if key == ord('q'): 
 print("Turning off camera.")  webcam.release()
 print("Camera off.")  print("Program ended.")  cv2.destroyAllWindows()  break 
from getkey import getkey, keys 
while 1: 
 key = getkey() 
 if key == keys.UP: 
 print("U") 
 elif key == keys.DOWN:  print("D") 
 elif key == keys.LEFT: 
 print("L") 
import time 
import RPi.GPIO as GPIO GPIO.setmode(GPIO.BOARD) Motor11 = 33 # Input1 Pin1 Motor12 = 31 # Input1 Pin2 Motor21 = 35 # Input2 Pin1 Motor22 = 37 # Input2 Pin2 IRleft = 16 # Left IR sensor IRright = 18 # Right IR sensor 
GPIO.setup(Motor11,GPIO.OUT) GPIO.setup(Motor12,GPIO.OUT) GPIO.setup(Motor21,GPIO.OUT)
GPIO.setup(Motor22,GPIO.OUT) GPIO.setup(IRleft,GPIO.IN) 
GPIO.setup(IRright,GPIO.IN) 
while True: 
 x=GPIO.input(IRleft) 
 y=GPIO.input(IRright) 
 print("IRL"+str(x)) 
 print("IRR"+str(y)) 
 '''GPIO.output(Motor11,GPIO.LOW)  GPIO.output(Motor12,GPIO.HIGH)  GPIO.output(Motor21,GPIO.LOW)  GPIO.output(Motor22,GPIO.HIGH)  time.sleep(2) 
 GPIO.output(Motor11,GPIO.LOW)  GPIO.output(Motor12,GPIO.LOW)  GPIO.output(Motor21,GPIO.LOW)  GPIO.output(Motor22,GPIO.LOW)''' 
 time.sleep(2)
