# Microsoft Azure IoT Suite

> What is Internet of Things? The Internet of Things (IoT) starts with your things—the things that matter most to your business. IoT is about making your data come together in new ways. Tap into data with IoT dashboards. Uncover actionable intelligence. And modernize how you do business. Welcome to the Internet of your Things. [Internet of Things](https://www.microsoft.com/en-us/server-cloud/internet-of-things/)

> Azure IoT Suite. Capture and analyze untapped data to improve business results. [Azure IoT Suite](https://azure.microsoft.com/en-us/solutions/iot-suite/)

- [IoT Suite documentation](https://azure.microsoft.com/en-us/documentation/suites/iot-suite/)

## Areas

> Tap into the Internet of your things with Azure IoT Suite. Azure IoT Suite brings the Internet of your things to life. Connect your devices, analyze previously-untapped data, and integrate business systems—and transform your company when you uncover new business models and revenue streams. [Azure IoT Suite](https://www.microsoft.com/en/server-cloud/internet-of-things/azure-iot-suite.aspx)

> IoT solutions transform the oil and gas industry. Giving cities a lift with IoT solutions. Enterprise IoT creates a connected commute. Driving automation with IoT solutions.  [IoT solutions transform the oil and gas industry](https://www.microsoft.com/en/server-cloud/internet-of-things/industry-solutions.aspx)

> Rely on expert IoT partners. Get ready to unleash true business value with the Internet of Things (IoT). Whether you’re building your own solution with certified devices, or looking for a complete IoT solution, get connected with a trusted partner that can help tailor the Azure IoT Suite to your industry-specific needs. [Partners](https://www.microsoft.com/en/server-cloud/internet-of-things/partners.aspx)


```sh
root@edison:~# npm install azure-iot-device
```

```sh
root@edison:~# cat azure.js
var device = require('azure-iot-device');
String = '[IoT Device Connection String]';
var client = new device.Client(connectionString, new device.Https());
var data = JSON.stringify({ 'deviceId': 'myFirstDevice', 'data': 'mydata' });
var message = new device.Message(data);
message.properties.add('myproperty', 'myvalue');
client.sendEvent(message, function(err, res){
    if (err) console.log('SendEvent error: ' + err.toString());
    if (res) console.log('SendEvent status: ' + res.statusCode + ' ' + res.statusMessage);
});
client.receive(function (err, res, msg) {
  console.log('receive data: ' + msg.getData());
  client.complete(msg, function(err, res){
    if (err) console.log('Complete error: ' + err.toString());
    if (res) console.log('Complete status: ' + res.statusCode + ' ' + res.statusMessage);
  });
});
```