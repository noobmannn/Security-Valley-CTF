# Security Valley CTF - The loader

![App Screenshot](https://github.com/shiroyagi4777/Security-Valley-CTF/blob/e4653fea106362d06af7f56a77526ee12acc1e0d/Reverse/The%20loader/Image/Screenshot%202023-06-17%20153736.png)

# Description

I've seen that in malware before. There must be something inside

Link: https://github.com/SecurityValley/PublicCTFChallenges/tree/master/reversing/the_loader

# Resources

https://github.com/SecurityValley/PublicCTFChallenges/tree/master/reversing/the_loader

crackme-03

# Solution

Đầu tiên mình sẽ dùng gdb để debug file trên, đặt breakpoint tại <main+102> và chạy chương trình:

![App Screenshot](https://github.com/shiroyagi4777/Security-Valley-CTF/blob/e4653fea106362d06af7f56a77526ee12acc1e0d/Reverse/The%20loader/Image/1.png)

Tiếp tục đi vào hàm huuu và trace đến hàm load_s_men:

![App Screenshot](https://github.com/shiroyagi4777/Security-Valley-CTF/blob/e4653fea106362d06af7f56a77526ee12acc1e0d/Reverse/The%20loader/Image/2.png)

Gõ 'finish' để thoát khỏi hàm load_s_men sau đó quan sát sự thay đổi giá trị trong các thanh ghi, chúng ta đã tìm thấy Flag :)))

![App Screenshot](https://github.com/shiroyagi4777/Security-Valley-CTF/blob/e4653fea106362d06af7f56a77526ee12acc1e0d/Reverse/The%20loader/Image/3.png)

# Flag

SecVal{w4Y_70_h4rD_F0R_Y0U}

