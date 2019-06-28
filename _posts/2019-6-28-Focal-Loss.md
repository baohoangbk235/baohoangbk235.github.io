---
layout: post
title: Web services là gì?
subtitle: Tổng quan về Focal Loss
gh-badge: [star, fork, follow]
tags: [web service]  
comments: true
---

Những mô hình nhận diện vât thể chính xác nhất đến nay được xây dựng dựa trên cách tiếp cận two-stage mà điển hình là R-CNN. Các mô hình này thường được dùng với một tập các object nằm khá thưa thớt và rải rác, trái ngược với phương pháp one-stage, thường được sử dụng cho các tập mẫu object có vị trí phân bố đồng đều và dày đặc.Mô hình sử dụng phương pháp one-stage thường nhanh và đơn giản hơn, tuy nhiên lại không chính xác bằng two-stage. Lí do cho việc này là sự không cân bằng giữa các foreground và background class gặp phải trong quá trình huấn luyện. Trong bài viết này, mình sẽ trình bày một giải pháp để giải quyết vấn đề trên, đó chính là sử dụng Focal Loss. Bài viết được tham khảo từ:https://arxiv.org/pdf/1708.02002.pdf và https://medium.com/@ManishChablani/focal-loss-for-dense-object-detection-paper-summary-79a030798e42
