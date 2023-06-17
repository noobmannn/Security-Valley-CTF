# Security Valley CTF - The loader

# Description

I've seen that in malware before. There must be something inside

Link: https://github.com/SecurityValley/PublicCTFChallenges/tree/master/reversing/the_loader

# Resources

https://github.com/SecurityValley/PublicCTFChallenges/tree/master/reversing/the_loader

crackme-03

# Solution

Đầu tiên mình sẽ dùng gdb để debug file trên, đặt breakpoint tại <main+102> và chạy chương trình:



Tiếp tục đi vào hàm huuu và trace đến hàm load_s_men:



Gõ 'Finish' để thoát khỏi hàm load_s_men sau đó quan sát sự thay đổi giá trị trong các thanh ghi, chúng ta đã tìm thấy Flag :)))



# Flag

SecVal{w4Y_70_h4rD_F0R_Y0U}

