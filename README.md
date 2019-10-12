# beetleC HTML Mod

Mod from [official sample](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Hat/beetleC/stickC/beetleC)

![UI](./UI.jpg)

- Joystick UI
- Weighted average calculation for smooth driving

# Procedure

## Endocing html to page.h 

> gzip -c page.html | xxd -i > page.hex

Copy array to page.h. 

## Calcurate buffer size automatically.

Edit beetleC.ino.

```
esp_err_t controlPage(httpd_req_t *req) {
    httpd_resp_set_type(req, "text/html");
    httpd_resp_set_hdr(req, "Content-Encoding", "gzip");
    return httpd_resp_send(req, (const char *)ctlPage, sizeof ctlPage); // <-Edit!
}
```

## Acknowledgement

Following JoyStick library is embedded in the html with some modification.
https://github.com/bobboteck/JoyStick