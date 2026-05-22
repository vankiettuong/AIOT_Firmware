/*
  ESP32 AIoT firmware for Backend_AIOT_module_V1 and ML_module_V1.

  Required Arduino libraries:
  - ArduinoJson by Benoit Blanchon
  - PubSubClient by Nick O'Leary
  - DHT sensor library by Adafruit
  - Adafruit Unified Sensor

  MQTT flow:
  - Publish telemetry to devices/<device_id>/telemetry every 10 seconds.
  - Publish device state to devices/<device_id>/devicetwin.
  - Subscribe to ML setpoint on devices/<device_id>/ml-setpoint.
  - Subscribe to app/device commands on devices/<device_id>/command.
  - Publish app commands as control events on devices/<device_id>/control-events.

  Relay state is mapped to backend fields lamp_cmd/lamp_actual because the
  current backend schema stores one binary output under those field names.

  Example app commands to devices/<device_id>/command:
  {"source":"app","mode":"auto","setpoint":28.5}
  {"source":"app","mode":"manual","fan_pwm":180,"relay":true}
  {"source":"app","feedback":"too_hot"}
*/
