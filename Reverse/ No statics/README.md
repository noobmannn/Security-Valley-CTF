# Security Valley CTF - No statics

![App Screenshot](https://github.com/shiroyagi4777/Security-Valley-CTF/blob/2ed5d34ca5621667e5f959d6dfbc620750338fda/Reverse/%20No%20statics/Image/Screenshot%202023-06-17%20153014.png)

# Description

This time there is no static value inside...but you are the best. So crack it baby!

Link: https://github.com/SecurityValley/PublicCTFChallenges/tree/master/reversing/no_static

# Resources

https://github.com/SecurityValley/PublicCTFChallenges/tree/master/reversing/no_static

crackme-02

# Solution

Đầu tiên mình run thử file trên và nhập bừa một input bất kì:

![App Screenshot](https://github.com/shiroyagi4777/Security-Valley-CTF/blob/2ed5d34ca5621667e5f959d6dfbc620750338fda/Reverse/%20No%20statics/Image/2.png)

Mở file trên bằng IDA và phân tích Pseudocode của nó, mình nhận ra rằng hàm main đầu tiên sẽ in ra giá trị của s2 sau khi bị biến đổi bởi hàm prepare, sau đó so sánh input nhập vào mới giá trị của biến s2, và cuối cùng kiểm tra nếu hai chuỗi giống nhau thì in ra Flag, còn sai thì in 'WRONG!':

![App Screenshot](https://github.com/shiroyagi4777/Security-Valley-CTF/blob/2ed5d34ca5621667e5f959d6dfbc620750338fda/Reverse/%20No%20statics/Image/1.png)

Vì lúc mình nhập input bừa chương trình in ra dòng mySecret trước khi in Wrong, nên bây giờ mình sẽ nhập thử input là mySecret. Và đây là kết quả :)))

![App Screenshot](https://github.com/shiroyagi4777/Security-Valley-CTF/blob/2ed5d34ca5621667e5f959d6dfbc620750338fda/Reverse/%20No%20statics/Image/3.png)

# Flag

SecVal{Th15_Wa5_Hard3R}


