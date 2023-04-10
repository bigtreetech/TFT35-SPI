# Software Settings
## Work with raspberry pi
Note: Raspberry PI does not support the touch of this screen, only can display
* Disable KMS in `/boot/config.txt`
    ```
    #dtoverlay=vc4-kms-v3d
    ```
* Add the following to the raspberry pi `/boot/config.txt` file
    ```
    dtoverlay=fbtft,spi0-0,ili9486,width=320,height=480,dc_pin=25
    dtparam=cpha=1,cpol=1,speed=24000000,fps=60
    dtparam=bgr=1,rotate=90,txbuflen=307200
    ```
* The hardware wiring is as follows
    ```
    TFT35_SPI_CS=GPIO4
    TFT35_SPI_RS=GPIO25
    SPI_MOSI=GPIO10
    SPI_MISO=GPIO9
    SPI_CLK=GPIO11
    ```

## Work with CB1
1. Uncomment `overlays=tft35_spi` in `/boot/BoardEnv.txt`. <img src=Images/BoardEnv.png width="800" /><br/> <img src=Images/tft35_spi.png width="800" /><br/>
2. If the OS image of v2.2.1 version is used. Set to `overlays=tft35_spi25` instead of `overlays=tft35_spi` Use the SPI speed of 25Mhz instead of the default 50Mhz to avoid display confusion. If the OS image after V2.2.1 is used, The OS  will use a lower and more stable speed by default.
