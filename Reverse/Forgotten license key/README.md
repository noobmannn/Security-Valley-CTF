# Security Valley CTF - Forgotten license key

![App Screenshot](https://github.com/shiroyagi4777/Security-Valley-CTF/blob/4a71c5825328966c77e6a913798ae630006f21b6/Reverse/Forgotten%20license%20key/Image/Screenshot%202023-06-16%20132123.png)

# Description

Unfortunately, I forgot my license key. Fortunately, the program is somewhat chatty. Maybe together we can manage to recover the license key. Can you help me?

Link: https://github.com/SecurityValley/PublicCTFChallenges/tree/master/reversing/forgotten_license_key

# Resources
https://github.com/SecurityValley/PublicCTFChallenges/tree/master/reversing/forgotten_license_key

license

license.exe

# Solution

Đầu tiên mình sẽ chạy File license trên Terminal Linux. Mình nhận ra cần phải nhập một Key từ bàn phím.

![App Screenshot](https://github.com/shiroyagi4777/Security-Valley-CTF/blob/d08499c6703bae34021fb95af3d18a82275a6069/Reverse/Forgotten%20license%20key/Image/001.png)

Mình thử nhập bừa một giá trị nào đó:

![App Screenshot](https://github.com/shiroyagi4777/Security-Valley-CTF/blob/d08499c6703bae34021fb95af3d18a82275a6069/Reverse/Forgotten%20license%20key/Image/002.png)

Mở File license trên IDA, mở Subview String và tìm thử chuỗi 'wrong length'

![App Screenshot](https://github.com/shiroyagi4777/Security-Valley-CTF/blob/d08499c6703bae34021fb95af3d18a82275a6069/Reverse/Forgotten%20license%20key/Image/003.png)

Mình nhận ra chuỗi này được gọi tới tại hàm sub_57E5A0, đọc qua code Assembly, mình nhận ra Input đầu vào chỉ được phép nhập 9 kí tự, và sau khi nhập đúng, chương trình sẽ gọi đến hàm sub_57E700

![App Screenshot](https://github.com/shiroyagi4777/Security-Valley-CTF/blob/d08499c6703bae34021fb95af3d18a82275a6069/Reverse/Forgotten%20license%20key/Image/004.png)

Đọc và phân tích code Assembly tại hàm sub_57E700, mình nhận ra định dạng của Key cần đưa vào: kí tự đầu tiên, thứ năm và thứ bảy lần lượt luôn luôn là '7', '-' và 'D', tổng của ba kí tự thứ hai, thứ ba và thứ tư phải bằng 203 và tổng của ba kí tự thứ sáu, thứ tám và thứ chín phải là 214

Sẽ có rất nhiều Key thoả mãn các yêu cầu trên nên mình thử tìm 2 Key như vậy và nhập, có thể thấy kết quả in ra của mỗi lần nhập là khác nhau.

![App Screenshot](https://github.com/shiroyagi4777/Security-Valley-CTF/blob/d08499c6703bae34021fb95af3d18a82275a6069/Reverse/Forgotten%20license%20key/Image/005.png)

Từ đây mình sẽ Brute Force để tìm Key đúng

```python
import subprocess
import shlex


def bruteforce_license():
    stab = list("abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789")
    for key1 in stab:
        for key2 in stab:
            for key3 in stab:
                for key5 in stab:
                    for key7 in stab:
                        for key8 in stab:
                            sum_123 = ord(key1) + ord(key2) + ord(key3)
                            sum_578 = ord(key5) + ord(key7) + ord(key8)

                            if sum_123 == 203 and sum_578 == 214:
                                key_str = "7" + key1 + key2 + key3 + "-" + key5 + "D" + key7 + key8
                                command = "./license --key=" + shlex.quote(key_str)
                                try:
                                    output = subprocess.check_output(command, shell=True, stderr=subprocess.DEVNULL)
                                    output_str = output.decode().strip()

                                    if "SecVal" in output_str:
                                        print("Key found: " + key_str)
                                        print("Output: " + output_str)
                                        return
                                except subprocess.CalledProcessError:
                                    continue


bruteforce_license()
```
Và đây là kết quả :)))

![App Screenshot](https://github.com/shiroyagi4777/Security-Valley-CTF/blob/d08499c6703bae34021fb95af3d18a82275a6069/Reverse/Forgotten%20license%20key/Image/006.png)

# Flag
SecVal{go_r0ckz_m8!}
