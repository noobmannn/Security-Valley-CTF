# Security Valley CTF - The loader

![App Screenshot](https://github.com/shiroyagi4777/Security-Valley-CTF/blob/8a1fd1ea773d662de2764c2288b670d5e30681f1/Reverse/damn%20windows/Image/Screenshot%202023-06-17%20153906.png)

# Description

There is some exotic compiled windows executable.Can you deal with it?

Link: https://github.com/SecurityValley/PublicCTFChallenges/tree/master/reversing/damn_windows

# Resources

https://github.com/SecurityValley/PublicCTFChallenges/tree/master/reversing/damn_windows

01.exe

# Solution

Mở file bằng IDA, truy cập vào hàm main_main, quan sát kĩ ta sẽ thấy trong hàm này có lệnh call gọi tới hàm main___PasswordService__Validate

![App Screenshot](https://github.com/shiroyagi4777/Security-Valley-CTF/blob/8a1fd1ea773d662de2764c2288b670d5e30681f1/Reverse/damn%20windows/Image/1.png)

Quan sát hàm main___PasswordService__Validate, chúng ta sẽ thấy một vài String trông khá đáng ngờ. Giờ ta chỉ cần ghép chúng lại với nhau là được :)))

![App Screenshot](https://github.com/shiroyagi4777/Security-Valley-CTF/blob/8a1fd1ea773d662de2764c2288b670d5e30681f1/Reverse/damn%20windows/Image/2.png)

# Flag

SecVal{this_1S_n1ce}


