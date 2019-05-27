---
layout: post
title: Web services là gì?
subtitle: Những giới thiệu cơ bản về Web Services 
gh-badge: [star, fork, follow]
tags: [web service]  
comments: true
---

Khái niệm Web Service được sử dụng rất nhiều trong quá trình phát triển một ứng dụng, đặc biệt khi chuyển đổi một ứng dụng thông thường sang ứng dụng web. Đồng thời nó cũng xuất bản các chức năng của mình để mọi người dùng internet trên thế giới đều có thể sử dụng thông qua nền tảng web. Do đó, hôm nay chúng ta sẽ c 

## Web Service là gì

Các tài liệu và các cuốn sách khác nhau đưa ra những định nghĩa khác nhau về Web Services. Một vài ý chính có thể được liệt kê ra dưới đây.
* Một web service là bất cứ phần nào của phần mềm làm chính nó khả dụng qua internet (ở đây được hiểu là có khả năng truy cập và sử dụng qua internet) và sử dụng một hệ thống truyền tin XML tiêu chuẩn. XML được sử dụng để mã hóa tất cả các giao tiếp tới một web service. Ví dụ, một client gọi đến một web service bằng việc thực hiện gửi một tập tin XML, rồi đợi thông điệp hồi đáp dưới dạng XML tương ứng. Vì tất cả các giao tiếp là trong XML, web services không bị bó buộc bởi bất cứ hệ điều hành hay ngôn ngữ lập trình nào - Java có thể nói chuyện được với Python; các ứng dụng trên Windows có thể giao tiếp được với các ứng dụng trên Linux một các dễ dàng.
* Web Service là các ứng dụng động, phân tán, mô-đun và khép kín. Do đó chúng có thể được mô tả, công bố rộng rãi, định vị hay gọi tới qua mạng để tạo các sản phẩm, quy trình hay chuỗi cung ứng. Các ứng dụng này có thể local, phân tán hoặc xây dựng trên web. Web Service được xây dựng ở phần trên của các chuẩn mở như TCP/IP, HTTP, Java, HTML và XML.
* Web Services là các hệ thống trao đổi thông tin bằng XML sử dụng internet cho việc tương tác trực tiếp giữa ứng dụng với ứng dụng. Hệ thống này có thể bao gồm các chương trình, đối tượng, tệp tin và văn bản.
* Một web service là một tập hợp các giao thức và chuẩn sử dụng cho việc trao đổi dữ liệu giữa các ứng dụng và hệ thống. Các ứng dụng phần mềm được viết bằng các ngôn ngữ lập trình khác nhau và chạy trên các nền tảng khác nhau có thể sử dụng web services để trao đổi dữ liệu qua các mạng máy tính như Internet bằng cách thức tương tự như việc giao tiếp giữa các tiến trình nội bộ trong một máy tính bình thường. Khả năng tương tác này (ví dụ: giữa Java và Python, giữa các ứng dụng Windows và các ứng dụng Linux) là dựa vào việc sử dụng các chuẩn mở.


**Để tổng kết lại thì, web services là bất cứ dịch vụ nào mà**
* *Khả dụng qua internet hoặc mạng cá nhân (nội bộ)*
* *Không bị phụ thuộc vào bất cứ hệ điều hành hoặc ngôn ngữ lập trình nào*
* *Tự mô tả được thông qua các cú pháp XML phổ thông*
* *Có thể phát hiện bởi cơ chế tìm kiếm đơn giản*


## Các thành phần của Web Services
Một nền tảng web service cơ bản là XML + HTTP. Tất cả các web services tiêu chuẩn đều sử dụng các thành phần sau:
* SOAP (Giao thức truy cập đối tượng đơn giản)
* UDDI (Universal Description, Discovered and Integrated)
* WSDL (Web Services Desription Language): Ngôn ngữ mô tả WS

## Web Service hoạt động như thế nào
Một web service cho phép giao tiếp giữa các ứng dụng hoạt động bằng cách sử dụng các chuẩn mở như HTML, XML, WSDL và SOAP. Một web service cần đến sự trợ giúp của
* XML để dán nhãn dữ liệu
* SOAP để truyền tập tin
* WSDL để mô tả tính khả dụng của service

Chúng ta có thể  sử dung C# để xây dựng một web service mới trên Windows mà nó có thể gọi tới từ ứng dụng web bằng JavaServer Pages (JSP) chạy trên Linux.

## Ví dụ
 Xét một hệ thống đơn giản quản lý tài khoản và xử lý các yêu cầu. Nhân viên kế toán sử dụng một client app xây dựng với Visual Basic hay JSP để tạo account mới và nhập vào yêu cầu của khách hàng.
 
 Giả sử hệ thống này được viết trong Java và đặt ở trên một máy Solaris, đồng thời thực hiện việc tương tác với database để lưu trữ thông tin.
 
 ![Quá trình một web service đơn giản hoạt động](http://tutorials.jenkov.com/images/web-services/web-service-message-formats-1.png)
 
 Các bước để thực hiện như sau:
 * Chương trình ở phía client sẽ gán thông tin đăng kí tài khoản vào một gói tin SOAP.
 * Gói tin SOAP này được gửi tới web service dưới dạng body của một HTTP POST request.
 * Web service giải nén SOAP request và chuyển nó thành một câu lệnh mà ứng dụng có thể hiểu được.
 * Ứng dụng xử lý thông tin được yêu cầu và hồi dáp một con số đặc biệt cho tài khoản của khách hàng được tạo.
 * Tiếp theo, web service sẽ gói request vào một gói tin SOAP khác, gói tin này sẽ được gửi lại chương trình client để phản hồi về cho HTTP request của nó.
 * Chương trình client giải nén gói tin SOAP để nhận kết quả của quá trình đăng kí tài khoản khách hàng.
