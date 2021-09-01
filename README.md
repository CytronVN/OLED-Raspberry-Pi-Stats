# OLED-Raspberry-Pi-Stats
Hiển thị thông tin về CPU, RAM, nhiệt độ và IP của Raspberry Pi trên màn hình OLED I2C hoặc SPI

1. Bật interface I2C bằng lệnh
```sudo raspi-config```
2. Cài đặt các thư viên liên quan, ví dụ như smbus, Adafruit_BBIO
```
sudo apt-get install python-smbus
sudo apt-get install i2c-tools
sudo pip3 install Adafruit_BBIO
```
3. Kiểm tra kết nối I2C
```
sudo i2cdetect -y 1
```
4. Tải bộ thư viện & code mẫu cho màn hình SSD1306
```
sudo python -m pip install --upgrade pip setuptools wheel
git clone https://github.com/adafruit/Adafruit_Python_SSD1306.git
```
5. Cài đặt
```
cd Adafruit_Python_SSD1306
sudo python3 setup.py install
```
Lúc này, bạn có thể vào thư mục example để chạy thử các chương trình mẫu với python3

6. Tải đoạn code mẫu & font chữ đã tối ưu cho màn hình OLED từ Cytron

```
git clone https://github.com/CytronVN/OLED-Raspberry-Pi-Stats.git
```
7. Chạy chương trình
```
python3 stats.py
```
8. Cấu hình để script tự chạy mỗi khi Raspberry Pi khởi động với crontab
```
crontab -e
```

Nếu chưa chỉnh sửa crontab bao giờ, bạn sẽ được hỏi chọn 1 text editor. Hãy chọn Nano

Sau đó, thêm dòng này vào file
```
@reboot python3 /home/pi/stats.py &
```

Lưu file và khởi động lại Pi để kiểm tra.



