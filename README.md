# IoT-Mini-Project-1
IoT Mini Project 1


1	Read data from sensor.


2	Send data from M3 board to AWS IoT Core
2.1	Data Type
JSON 
Ex
{
  "temperature": 25.5,
  "humidity": 50.2,
  "status": "OK"
}
2.2	Prerequisites: 

2.2.1	AWS IoT Thing:

Set up an IoT Thing on AWS IoT Core.

2.2.2	Security Credentials:

Generate security credentials (access key ID and secret access key) with the necessary permissions for your IoT Thing.

2.3	Steps:

2.3.1	Download and Install AWS IoT Device SDK for C:

Download the AWS IoT Device SDK for C from the official AWS GitHub repository: aws-iot-device-sdk-c.
Follow the instructions in the repository to build and install the SDK on your M3 board.

2.3.2	Configure AWS IoT Device SDK:

Configure the AWS IoT Device SDK with your IoT Thing's endpoint, security credentials, and other necessary parameters.
#include "aws_iot_config.h"

// Configure AWS IoT endpoint and credentials
AWS_IOT_MY_ENDPOINT "your-iot-endpoint.iot.your-region.amazonaws.com"
AWS_IOT_ROOT_CA_FILENAME "your-root-ca.pem"
AWS_IOT_CERTIFICATE_FILENAME "your-certificate.pem.crt"
AWS_IOT_PRIVATE_KEY_FILENAME "your-private.pem.key"

2.3.3	Write Code to Publish Data:

Write C code on your M3 board to collect the data you want to send and publish it to AWS IoT Core.
#include "aws_iot_mqtt_client_interface.h"

// Initialize the MQTT client
AWS_IoT_Client client;

// Connect to AWS IoT Core
rc = aws_iot_mqtt_connect(&client);
if (rc == MQTT_SUCCESS) {
    // Publish data to a topic
    aws_iot_mqtt_publish(&client, "your/topic", strlen("your data payload"), "your data payload", 0, false);
}

// Disconnect from AWS IoT Core
aws_iot_mqtt_disconnect(&client);

2.3.4	Build and Run:

Build your C code with the AWS IoT Device SDK for C.
Deploy and run your code on your M3 board.

2.3.5	Monitor AWS IoT Core:

Monitor the AWS IoT Core console for incoming data from your device.

2.3.6	Notes:

Ensure that your M3 board has network connectivity and the necessary libraries for making secure connections.
Follow the documentation and examples provided by the AWS IoT Device SDK for C for more detailed information and advanced features.
Keep in mind that the exact implementation details may vary based on your M3 board and the SDK version you are using. Always refer to the documentation provided by your board's manufacturer and the AWS IoT SDK for the most accurate information.



3	Data visualization



