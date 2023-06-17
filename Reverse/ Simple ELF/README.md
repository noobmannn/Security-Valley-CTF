# Security Valley CTF - Simple ELF

![App Screenshot](https://github.com/shiroyagi4777/Security-Valley-CTF/blob/da8f13133c0dc5b9b9272339fe1aef4977795a8f/Reverse/%20Simple%20ELF/Image/Screenshot%202023-06-17%20152751.png)

# Description

Can you deal with dwarfs and elfs`

Link: https://github.com/SecurityValley/PublicCTFChallenges/tree/master/reversing/the_elf

# Resources

https://github.com/SecurityValley/PublicCTFChallenges/tree/master/reversing/the_elf

crackme-01

# Solution

Mở file bằng IDA, truy cập vào hàm main, quan sát kĩ ta sẽ thấy trong hàm này có lệnh call gọi tới hàm printFlag

![App Screenshot](https://github.com/shiroyagi4777/Security-Valley-CTF/blob/da8f13133c0dc5b9b9272339fe1aef4977795a8f/Reverse/%20Simple%20ELF/Image/1.png)

Quan sát hàm printFlag, chúng ta sẽ tìm thấy Flag :)))

![App Screenshot](https://github.com/shiroyagi4777/Security-Valley-CTF/blob/da8f13133c0dc5b9b9272339fe1aef4977795a8f/Reverse/%20Simple%20ELF/Image/2.png)

# Flag

SecVal{cr4ck1n9_15_E45y}

