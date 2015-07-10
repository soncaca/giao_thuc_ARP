# giao_thuc_ARP
Như đã biết trong mô hình OSI, gói tin ở lớp 3 có địa chỉ IP nguồn, địa chỉ IP đích sau đó sẽ được chuyển xuống lớp 2 đóng thành các frame trong đó có MAC đích và MAC nguồn rồi sau đó mới có thể  truyền thông tin giữa hai máy tính trong cùng một mạng vật lý 

<img src="http://i.imgur.com/ZvtsjE6.jpg">

- ARP là  là giao thức giúp ta xác định được địa chỉ MAC của máy tính khi biết địa chỉ IP.

Có hai dạng bản tin trong ARP : một được gửi từ nguồn đến đích, và một được gửi từ đích tới nguồn.
+ Request : Khởi tạo quá trình, gói tin được gửi từ thiết bị nguồn tới thiết bị đích
+ Reply : Là quá trình đáp trả gói tin ARP request, được gửi từ máy đích đến máy nguồn



### DEMO
Đây là sơ đồ demo giao thức ARP,kết quả mong muốn thu được sẽ là 2 máy sẽ  lưu được địa chỉ MAC của nhau vào MAC table của mỗi máy.
<img src="http://i.imgur.com/vRLmmIZ.png">

tôi dung công cụ tcpdump để kiểm tra việc liên lạc giữa 2 máy bằng giao thức ARP
<img src="http://i.imgur.com/fHBmNfh.png">

sau khi ở máy WinXP tôi thực hiên việc ping đến địa chỉ IP của máy Ubuntu chúng ta sẽ thấy . Đầu tiên, máy WinXP phát ra một gói tin ARP request (dạng broadcast) trên mạng yêu cầu tìm địa chỉ MAC của máy nào có IP là `192.168.1.19` mau trả lời lại cho địa chỉ `192.168.1.11` vì là gói tin broadcast nên các máy trên mạng sẽ nhận gói tin này và xử lý. Mỗi máy sẽ kiểm tra xem địa chỉ `192.168.1.19` có phải là IP của mình không. Nếu ko thì nó loại gói tin này. 

Trong trường hợp này máy Ubuntu nhận được đây đúng là địa chỉ IP của máy mình vì vậy nó sẽ lấy địa chỉ MAC của nó và gửi gói tin ARP reply (dạng unicast) về cho máy WinXP. Đồng thời máy Ubuntu cũng cập nhật vào MAC table địa chỉ IP và MAC của máy WinXP vào bảng MAC table của mình.Lúc này, máy WinXP đã có địa chỉ MAC của máy Ubuntu. Nó sẽ lưu và MAC table của nó.






