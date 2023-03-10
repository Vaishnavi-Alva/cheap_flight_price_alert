from twilio.rest import Client
import smtplib

TWILIO_SID = "AC57159f356aa8a93daf4cddd998938c56"
TWILIO_AUTH_TOKEN = "6e4ac0db6f5f8fdf68a87cfb7675acb9"
TWILIO_VIRTUAL_NUMBER = "+18644007766"
TWILIO_VERIFIED_NUMBER = "+919892827387"
MAIL_PROVIDER_SMTP_ADDRESS = "smtp.gmail.com"
MY_EMAIL = "raxisrashid@gmail.com"
MY_PASSWORD = "spjqvjslxcvgviek"


class NotificationManager:

    def __init__(self):
        self.client = Client(TWILIO_SID, TWILIO_AUTH_TOKEN)

    def send_sms(self, message):
        message = self.client.messages.create(
            body=message,
            from_=TWILIO_VIRTUAL_NUMBER,
            to=TWILIO_VERIFIED_NUMBER,
        )
        print(message.sid)

    def send_emails(self, emails, message, google_flight_link):
        with smtplib.SMTP(host=MAIL_PROVIDER_SMTP_ADDRESS, port=587) as connection:
            connection.starttls()
            connection.login(MY_EMAIL, MY_PASSWORD)
            for email in emails:
                connection.sendmail(
                    from_addr=MY_EMAIL,
                    to_addrs=email,
                    msg=f"Subject:New Low Price Flight!\n\n{message}\n{google_flight_link}".encode('utf-8')
                )
