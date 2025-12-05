From the [previous homework](homework-07.md), you need to add the following endpoint to the generated base64 string before passing them to the qrcode generater function. So the if the generated base64 is (for example):
```
aGVhbHRoZGVhbHNhdGlzZmllZG5vcnRoYWdhaW5zdHNoYXJldHJhY2tzeW1ib2xwcmU=
```
Then the full string that you should be passed to the qrcode function generator is:
```
https://ddd05aafa0b5.ngrok-free.app/journal/aGVhbHRoZGVhbHNhdGlzZmllZG5vcnRoYWdhaW5zdHNoYXJldHJhY2tzeW1ib2xwcmU=
```

