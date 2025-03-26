# Image-Caption
Để giải quyết bài toán image captioning thì í tưởng cơ bản  là áp dụng mạng ResNet50 làm bộ mã hóa để tạo biểu diễn vectơ một chiều của hình ảnh đầu vào. Sau đó, để sinh ra các câu mô tả, chúng em lấy LSTM làm mô hình ngôn ngữ để bộ giải mã giải mã vector thành câu. Trong khi đó, chúng em sử dụng soft attention trong bộ giải mã để cho phép mô hình tập trung  attention có chọn lọc vào một phần nhất định của hình ảnh nhằm dự đoán câu tiếp theo tốt hơn và bên cạnh đó thêm trường hợp không sử dụng soft attention.
## 1.Mô hình CNN-LTSM:
- Huấn luyện mô hình bằng cách sử dụng phương pháp giảm gradient descent ngẫu nhiên. Trong phương pháp encoder-decoder, có khả năng hình ảnh được xác định bằng cách tối đa hóa hàm khả năng logarit của biểu thức S, xem xét hình ảnh I tương ứng và các tham số của mô hình θ
  
![image](https://github.com/user-attachments/assets/f4d88f58-9560-46ef-b1ed-7ad7109a151d)

Trong đó θ là tham số của mô hình, I là hình ảnh đầu vào và S là mô tả chính xác. Vì S đại diện cho một câu có độ dài bất kỳ, do đó, quy tắc dây chuyền thường được sử dụng để lập mô hình xác suất chung trên S1, ⋯, SN, trong đó N là độ dài của ví dụ cụ thể này.

![image](https://github.com/user-attachments/assets/f9974649-8aac-4447-932e-33bca532e92d)

-Trong đó sự phụ thuộc vào θ được bỏ qua để thuận tiện. Việc huấn luyện mạng được biểu thị bằng cặp (S, I) và chúng em tối ưu hóa tổng các hàm log, trên toàn bộ tập huấn luyện bằng cách sử dụng phương pháp giảm độ dốc ngẫu nhiên.

![image](https://github.com/user-attachments/assets/95f6c63d-c53e-43cf-b855-ec30f992edad)

-Để thể hiện hình ảnh, chúng em sử dụng mạng ResNet50 - một mạng CNN sâu 50 lớp. Độ sâu của mạng giúp tăng hiệu suất nhưng cũng khó đào tạo. Cấu trúc của ResNet50 cho phép đào tạo mạng sâu hơn, dẫn đến hiệu suất cao hơn và số lượng tham số nhỏ hơn so với các mạng đơn giản.

![image](https://github.com/user-attachments/assets/13729759-2194-4803-8a3e-7b91b8076970)

DATA:https://drive.google.com/drive/folders/15ULMU3CN3dT3LIU4FEX4TVnoyyPHKZu6?usp=drive_link
