---
layout: post
title: Các tính chất hướng đối tượng của Java
subtitle: Những tính chất hướng đối tượng của Java
tags: []
comments: true
---
## Tính kế thừa
Trong lập trình hướng đối tượng, các chương trình máy tính được thiết kế sao cho mọi thứ đều là một object, và chúng sẽ thực hiện tương tác với nhau. Tính kế thừa ở đây cũng có thể được hiểu theo khía cạnh này, khi một thuộc tính của một lớp nào đó có thể được thừa kế bởi một lớp khác. Điều này đặc biệt hữu dụng trong việc tái sử dụng code và thiết lập mối quan hệ giữa các classes khác nhau, sẽ giúp code của bạn gọn gàng và dễ đọc hơn.

![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2017/04/Inheritance-1-468x300.png)

Như chúng ta có thể thấy trong hình vẽ,ông con thừa hưởng một số đặc tính của ông cha,ví dụ như tóc đều có màu nâu, mắt đều xanh dương, hàm én mày ngài,trán cao mũi hếch,vv... Tương tự, trong Java Lớp Con sẽ thừa hưởng các thuộc tính và phương thức mà Lớp Cha đang có. 

Thừa kế được chia ra làm 4 loại chính, bạn có thể xem trong hình vẽ: Đơn thừa kế, Đa thừa vế, Thừa kế thứ bậc và thừa kế hỗn hợp.

![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2017/04/Inheritance-types-java.png)

Nãy giờ chúng ta đang nói chung chung về các khái niệm. Vậy thì làm sao để thể hiện sự kế thừa trong Java? Trong Java, để thể hiện một lớp muốn kế thừa từ một lớp nào đó, bạn sử dụng từ khóa **extends**.

```java
class HinhTron {
    float bk;
    float getBanKinh() {
        return bk;
    }
}
 
class HinhTru extends HinhTron {
 
}
```

## Tính đóng gói (Encapsulation)




