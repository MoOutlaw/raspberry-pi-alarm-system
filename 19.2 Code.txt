from gpiozero import MotionSensor, LED, Buzzer
import time
import smtplib
from email.mime.text import MIMEText
from email.mime.multipart import MIMEMultipart
 
# Set a variable to hold the GPIO Pin identity
pir = MotionSensor(17)
red = LED(18)
blue = LED(24)
buzzer = Buzzer(22)
 
# Email configuration
sender = "covcollegelab@gmail.com"  # Change to your sender email
password = "irsn xidp xuoi kags"  # Replace with your app password
receiver = "###"  # Change to the receiver email
 
def send_email(receiver, subject, body):
    msg = MIMEMultipart()
    msg["From"] = sender
    msg["To"] = receiver
    msg["Subject"] = subject
 
    msg.attach(MIMEText(body, "plain"))
 
    try:
        with smtplib.SMTP("smtp.gmail.com", 587) as server:
            server.starttls()
            server.login(sender, password)
            server.sendmail(sender, receiver, msg.as_string())
        print("Email sent successfully!")
    except Exception as e:
        print(f"Error: {e}")
 
# Wait for PIR sensor to settle
print("Waiting for PIR to settle")
pir.wait_for_no_motion()
print("PIR Module Test (CTRL-C to exit)")
 
# Variables to hold the current and last states
currentstate = False
previousstate = False
 
try:
    # Loop until user quits with CTRL-C
    while True:
        # Read PIR state
        currentstate = pir.motion_detected
 
        # If the PIR is triggered
        if currentstate and not previousstate:
            print("Motion detected!")
            # Send email alert
            send_email(receiver, "Motion Alert", "Motion has been detected by the PIR sensor. Please check the area.")
 
            # Flash lights and sound buzzer three times
            for _ in range(3):
                buzzer.on()
                red.on()
                time.sleep(0.5)
                red.off()
                blue.on()
                time.sleep(0.5)
                blue.off()
                buzzer.off()  # Ensure buzzer is turned off after each flash
                time.sleep(0.3)
 
            # Record previous state
            previousstate = True
 
        # If the PIR has returned to the ready state (no motion)
        elif not currentstate and previousstate:
            print("No Motion")
            previousstate = False
 
        # Wait for 10 milliseconds
        time.sleep(0.01)
 
except KeyboardInterrupt:
    print("Quit")