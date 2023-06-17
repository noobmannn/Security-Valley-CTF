# Security Valley CTF - The loader

![App Screenshot]()

# Description

There is some exotic compiled windows executable.Can you deal with it?

Link: https://github.com/SecurityValley/PublicCTFChallenges/tree/master/reversing/damn_windows

# Resources

https://github.com/SecurityValley/PublicCTFChallenges/tree/master/reversing/damn_windows

01.exe

# Solution

Mở file bằng IDA, truy cập vào hàm main_main, quan sát kĩ ta sẽ thấy trong hàm này có lệnh call gọi tới hàm main___PasswordService__Validate

![App Screenshot]()

Quan sát hàm main___PasswordService__Validate, chúng ta sẽ thấy một vài String trông khá đáng ngờ. Giờ ta chỉ cần ghép chúng lại với nhau là được :)))

![App Screenshot]()

# Flag

SecVal{this_1S_n1ce}


