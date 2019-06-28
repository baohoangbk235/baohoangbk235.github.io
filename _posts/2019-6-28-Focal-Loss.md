---
layout: post
title: Focal Loss
subtitle: Tổng quan về Focal Loss
gh-badge: [star, fork, follow]
tags: [web service]  
comments: true
---

Những mô hình nhận diện vât thể chính xác nhất đến nay được xây dựng dựa trên cách tiếp cận two-stage mà điển hình là R-CNN. Các mô hình này thường được dùng với một tập các object nằm khá thưa thớt và rải rác, trái ngược với phương pháp one-stage, thường được sử dụng cho các tập mẫu object có vị trí phân bố đồng đều và dày đặc.Mô hình sử dụng phương pháp one-stage thường nhanh và đơn giản hơn, tuy nhiên lại không chính xác bằng two-stage. Lí do cho việc này là sự không cân bằng giữa các foreground và background class gặp phải trong quá trình huấn luyện. Trong bài viết này, mình sẽ trình bày một giải pháp để giải quyết vấn đề trên, đó chính là sử dụng Focal Loss. Bài viết được tham khảo từ:https://arxiv.org/pdf/1708.02002.pdf và https://medium.com/@ManishChablani/focal-loss-for-dense-object-detection-paper-summary-79a030798e42

**Tổng quan**: Focal loss được sử dụng bằng việc thay đổi một chút hàm cross-entropy nhằm giảm trọng số đối mất mát của các object được phân loại tốt. Thay vào đó, nó sẽ tập trung vào các trường hợp khó hơn, nhằm tránh việc các trường hợp dễ sẽ gây ảnh hưởng quá lớn đến mô hình, dẫn đến giảm hiệu quả khi huẩn luyện.

Focal Loss được đưa ra để giải quyết trong trường hợp có sự mất cân bằng lớn giữa các foreground và background classes trong huấn luyện, chẳng hạn 1:1000.

**Focal Loss**
![](https://fmlcb.s3.dualstack.us-east-2.amazonaws.com/original/2X/9/91fb7f6e974747f7a94906d55fe66bbf8a63ba63.png)

Cross Entropy :Để bắt đầu thì chúng ta nhắc lại định nghĩa hàm cross-entropy (CE) cho binary classification: 

![](https://fmlcb.s3.dualstack.us-east-2.amazonaws.com/original/2X/7/768164e621e5042e8ccfdf2a71c972b947019211.jpeg)
Trong hàm trên thì y nhận giá trị 1 hoặc -1 biểu diễn ground-truth class và p nằm trong khoảng (0,1) là xác suất dự đoán cho class với y =1. Để cho thuận tiện ta định nghĩa lại hàm trên: 
![](https://fmlcb.s3.dualstack.us-east-2.amazonaws.com/original/2X/3/33ff02e9d495d021659f2f5c227f44b090ed9af5.png)

Cross-entropy có thể được biểu diễn bởi đường màu xanh da trời trong hình 1. Có thể dễ dàng nhận thấy là với các trường hợp được phân loại tốt ( xác suất lớn hơn hoặc bằng 0.6) thì hàm loss nhận giá trị với độ lớn lớn hơn 0, và khi tính tổng các số hạng này sẽ cho ra một số rất lớn so với loss của các trường hợp khó phân loại, và có thể làm ảnh hưởng đến quá trình huấn luyện.

- **Định nghĩa hàm focal loss**: Chúng ta sẽ thêm một nhân tử vào phía trước hàm cross-entropy, được gọi là modulating factor, với gamma lớn hơn hoặc bằng 0 được gọi là tham số focussing có thể điều chỉnh được :

![](https://forum.machinelearningcoban.com/uploads/default/optimized/2X/8/8609858dda85fa12f4a9f8ae3ca16b4a97f6dabb_2_690x88.jpeg)

- Quay trở lại hình 1 ban đầu, hàm focal loss được mô tả với các giá trị khác nhau của gamma với các giá trị từ 0 đến 5, trong đó với 0 chính là hàm cross-entropy như đã được mô tả bên trên. Chúng ta chú ý đến 2 tính chất của hàm focal loss:
Khi một mẫu bị phân loại sai và pt nhỏ, modulating factor gần 1 và loss sẽ không bị ảnh hưởng. Còn khi pt tiến tới 1, tức các trường hợp được phân loại tốt, moduling factor sẽ tiến tới 0 và hàm loss trong trường hợp này sẽ bị giảm trọng số xuống.

  - Tham số focusing gamma sẽ điều chỉnh tỷ lệ các trường hợp được phân loại tốt được giảm trọng số. Khi gamma càng tăng thì ảnh hưởng của *modulating factor cũng tăng. Thực nghiệm cho thấy với gamma = 2 thì kết quả đạt được sẽ tốt nhất.

  - Focal Loss thường được sử dụng kết hợp với Feature Pyramid Network trong RetinaNet. Kết quả khi so sánh RetinaNet sử dụng focal loss của chúng ta với các mô hình two-stage và one-stage không sử dụng focal loss khác:

![](https://forum.machinelearningcoban.com/uploads/default/optimized/2X/b/b84e1a287302135a8379e708919b37524d2f63c3_2_690x429.png)


- Trên đây là một vài tổng quan về **Focal Loss**. Tựu chung lại thì focal loss được sử dụng để giải quyết sự mất cân bằng giữa các foreground và background classes, là nguyên nhân chính khiến cho mô hình sử dụng one-stage chưa hiệu quả. Cảm ơn các bạn đã đọc bài viết, còn nhiều thiếu sót nên rất mong ý kiến đóng góp từ mọi người. Lần tới mình sẽ quay trở lại với những chi tiết hơn về Feature Pyramid Network và RetinaNet, mong nhận được sự ủng hộ của các bạn.
