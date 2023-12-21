# Philips Hue Random Notes

## How read temperature value of Philips Hue Motion Sensor

- Get Philips Hue bridge IP (written in mobile app for example under My system Hue and info button)
- Go to [http://\<found bridge IP\>/debug/clip.html]()
- Generate username via api `POST` request `/api` with body `{"devicetype":"my_hue_app#android device"}` send, click the button on the top of the bridge, send `POST` again
- Use the generated username and read all sensor values /api/<generated username>/sensors (ctrl + F temperature)
- Then one-liner using `curl` for found sensors temperature value is:

```
echo "scale=2; $(curl -s http://<found bridge IP>/api/<generated username>/sensors/30 | jq .state.temperature)/100" | bc -l
```
