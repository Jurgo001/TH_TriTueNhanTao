# BÁO CÁO THỰC HÀNH MÔN TRÍ TUỆ NHÂN TẠO
Sinh viên: Trương Khả Hào - MSSV: 2001230214
Link Source Code:(https://github.com/Jurgo001/TH_TriTueNhanTao.git)
## TỔNG QUAN
Em chọn thực hiện 3 bài sau:
1. Bài 1: Thuật toán tìm đường đi: AKT và A*
2. Bài 2: Giải thuật tìm kiếm đối kháng bao gồm: minimax, cắt tỉa alpha-beta.
3. Bài 3: Thuật toán K-mean, KNN.
## CHI TIẾT TỪNG BÀI

### 1. THUẬT TOÁN TÌM ĐƯỜNG ĐI: AKT VÀ A*
Vị trí code: Thư mục `Buoi01_02.ipynb`

BÀI 1: GIẢI BÀI TOÁN N-PUZZLE (TRÒ CHƠI TRƯỢT SỐ)
1. Cách chạy chương trình
   Bước 1: Mở file tại colab.
   Bước 2: chạy file.
2. Thông số động (Dynamic Input)Chương trình cho phép người dùng tương tác trực tiếp:
   Nhập kích thước N: Người dùng nhập số nguyên (Ví dụ: nhập 3 cho bàn 8-puzzle, 4 cho 15-puzzle).
   Chọn chế độ:Chế độ 1: Tự nhập tay ma trận ban đầu.Chế độ 2: Máy tự động tạo đề bài ngẫu nhiên (có thể chọn độ khó qua số bước xáo trộn).
3. Giải thích thuật toán & CodeTôi sử dụng thuật toán *A (A-Star) để tìm lời giải tối ưu nhất.
   Class HangDoiUuTien: Sử dụng Min-Heap để luôn lấy ra trạng thái có chi phí thấp nhất (F bé nhất) để duyệt trước.
   Class Nut (Node): Đại diện cho trạng thái bàn cờ.$G(n)$: Số bước đã đi từ đầu đến hiện tại. H(n) (Heuristic): Hàm tinh_chi_phi_h đếm số ô nằm sai vị trí so với đích.
   F(n) = G(n) + H(n): Tổng chi phí dự đoán.
   Hàm giai_puzzle_akt:Duyệt vòng lặp while đến khi tìm thấy đích hoặc hết khả năng tìm.
   Sử dụng TrangThai_DaTham (Closed Set) để tránh duyệt lại các trạng thái cũ gây lặp vô tận.
4. Demo kết quả
<img width="564" height="429" alt="image" src="https://github.com/user-attachments/assets/332bc20d-53b5-418f-9430-f52f277ac9a6" />

<img width="420" height="587" alt="image" src="https://github.com/user-attachments/assets/02610550-d678-4809-a9de-21fd09f188a4" />

<img width="555" height="668" alt="image" src="https://github.com/user-attachments/assets/9fedba65-e403-49e5-ad7d-31b34f5f6ed3" />

BÀI 2: TÌM ĐƯỜNG ĐI NGẮN NHẤT TRÊN ĐỒ THỊ (A*)
1. Cách chạy chương trình
   Bước 1: Mở file tại colab.
   Bước 2: chạy file.
2. Thông số động (Dynamic Input) Chương trình hỗ trợ nhập liệu linh hoạt cho bất kỳ đồ thị nào:
   Nhập cấu trúc đồ thị: Nhập theo cú pháp Đỉnh_Gốc Đỉnh_Đích Trọng_số (Ví dụ: A B 6).
   Nhập Heuristic: Nhập giá trị ước lượng h(n) cho từng đỉnh.
   Chọn điểm: Tự do chọn điểm Bắt đầu và điểm Kết thúc.
3. Giải thích thuật toán
   Sử dụng A Graph Search* để tìm đường đi ngắn nhất.
   Class DoThi: Quản lý danh sách kề (Adjacency List).
   Hàm thuat_toan_a_sao:*
4. Demo kết quả
<img width="683" height="380" alt="image" src="https://github.com/user-attachments/assets/ea75320f-30d1-4703-a673-1b59f4bf31c7" />

### 2. GIẢI THUẬT TÌM KIẾM ĐỐI KHÁNG: MINIMAX, CẮT TỈA ALPHA-BETA.
Vị trí code: Thư mục `Buoi03.ipynb`

BÀI 1: ÁP DỤNG MINIMAX GIẢI GAME TIC-TAC-TOE
1. Cách chạy chương trình
   Bước 1: Mở file tại colab.
   Bước 2: chạy file.
2. Thông số động (Dynamic Input)Chương trình cho phép người dùng nhập các thông số để thiết lập cây trò chơi:
   Nhập kích thước N: Xác định độ sâu và độ rộng của cây trò chơi (Ví dụ: N=3).
   Chọn phe (X/O): Xác định vai trò của máy là Max (X) hay Min (O).
   Nhập nước đi: Người dùng nhập tọa độ (i, j) để thay đổi trạng thái bàn cờ, kích hoạt máy tính lại nước đi mới.
3. Giải thích thuật toán: sử dụng thuật toán Minimax để xây dựng cây trò chơi và tìm nước đi tốt nhất dựa trên lý thuyết trò chơi đối kháng.
   Nguyên lý:MAX (AI): Luôn chọn nước đi có giá trị lớn nhất (cố gắng thắng, điểm +1).
   MIN (Người chơi): Giả định đối thủ luôn chọn nước đi làm cho AI bị điểm thấp nhất (cố gắng thua, điểm -1).
   Hàm đệ quy:gia_tri_toi_da(trang_thai): Duyệt tất cả các nước đi có thể, gọi đệ quy hàm gia_tri_toi_thieu và chọn giá trị max.
   gia_tri_toi_thieu(trang_thai): Duyệt tất cả các nước đi có thể, gọi đệ quy hàm gia_tri_toi_da và chọn giá trị min.
   Điều kiện dừng (ket_thuc): Khi có người thắng hoặc hòa, trả về điểm số tĩnh (Utility) cho trạng thái đó.
4. Demo kết quả
<img width="461" height="110" alt="image" src="https://github.com/user-attachments/assets/abd933e0-8e48-4db1-ad0a-2fd4983a94ae" />
<img width="523" height="514" alt="image" src="https://github.com/user-attachments/assets/ad337f55-0c37-4578-bfa7-8e1d7696f1fb" />
<img width="602" height="690" alt="image" src="https://github.com/user-attachments/assets/0cca6610-96b3-4507-8418-716a66966fa9" />

BÀI 3: CẢI TIẾN TỐC ĐỘ VỚI CẮT TỈA ALPHA-BETA
1. Cách chạy chương trình
   Bước 1: Mở file tại colab.
   Bước 2: chạy file.(Code đã tích hợp sẵn Alpha-Beta)
2. Thông số động (Dynamic Input)Tương tự bài Minimax, nhưng ở bài này ta có thể thử nghiệm với N lớn hơn (ví dụ N=4) để thấy sự khác biệt về hiệu suất:
   Nhập kích thước N: Thử nhập kích thước lớn để kiểm chứng tốc độ cắt tỉa.
   Chọn chế độ nhập tay: Để tạo ra các thế cờ mà nhánh cần cắt tỉa xuất hiện sớm.
3. Giải thích thuật toán: sử dụng kỹ thuật Alpha-Beta Pruning để tối ưu hóa thuật toán Minimax, giúp giảm không gian tìm kiếm.
   Tham số Alpha: Giá trị tốt nhất mà phe MAX đã đảm bảo được ở các nhánh trước đó.
   Tham số Beta: Giá trị tốt nhất mà phe MIN đã đảm bảo được ở các nhánh trước đó.
   Cơ chế Cắt tỉa (Pruning):
   Trong hàm gia_tri_toi_da: Nếu tìm thấy một giá trị v > \beta, tức là nhánh này quá tốt cho MAX nên MIN sẽ không bao giờ cho phép đi vào -> Cắt bỏ (Break loop).
   Trong hàm gia_tri_toi_thieu: Nếu tìm thấy một giá trị v < \alpha, tức là nhánh này quá tệ cho MAX (tốt cho MIN) nên MAX sẽ không bao giờ chọn đi vào -> Cắt bỏ (Break loop).
   Code: Dòng lệnh if alpha >= beta: break giúp thoát vòng lặp sớm, không cần duyệt các trạng thái con còn lại.
   4. Demo kết quả
<img width="561" height="306" alt="image" src="https://github.com/user-attachments/assets/dfbf6f97-a6aa-4ad1-85c0-ab533892e0cb" />

### 3. THUẬT TOÁN K-MEAN,KNN
Vị trí code: Thư mục `Buoi05.ipynb`

BÀI 1: PHÂN CỤM DỮ LIỆU TỰ ĐỘNG VỚI K-MEAN
1. Cách chạy chương trình
   Bước 1: Mở file tại colab.
   Bước 2: chạy file.
2. Thông số động (Dynamic Input)Chương trình cho phép người dùng tương tác để gom nhóm dữ liệu:
   Nhập Số Cụm (K): Người dùng nhập số nguyên dương K (Ví dụ: 3, 4, 5)->Đây là tham số quan trọng nhất, quyết định số lượng nhóm mà thuật toán sẽ cố gắng chia dữ liệu thành.
3. Giải thích thuật toán Tôi sử dụng thuật toán K-Means Clustering (Học không giám sát) để phân nhóm dữ liệu dựa trên khoảng cách.
   Tạo dữ liệu mẫu: Sử dụng phân phối chuẩn (Gaussian) để tạo ra các điểm dữ liệu phân tán ngẫu nhiên xung quanh các tâm giả định.
   Khởi tạo (khoi_tao_tam_cum): Chọn ngẫu nhiên K điểm trong tập dữ liệu làm tâm cụm ban đầu.
   Vòng lặp K-Means (Lặp đến khi hội tụ):
     Bước 1 (E-Step - Gán nhãn): Tính khoảng cách từ mỗi điểm dữ liệu đến tất cả các tâm cụm (dùng cdist). Điểm dữ liệu được gán vào cụm có tâm gần nhất.
     Bước 2 (M-Step - Cập nhật tâm): Tính toán lại vị trí tâm cụm mới bằng cách lấy trung bình cộng (Mean) tọa độ của tất cả các điểm thuộc cụm đó.
   Điều kiện dừng (np.allclose): Thuật toán dừng lại khi vị trí các tâm cụm không thay đổi sau một bước lặp (Hội tụ).
4. Demo kết quả
<img width="703" height="512" alt="image" src="https://github.com/user-attachments/assets/149d5f34-bc4d-47e6-9a7e-de7c4b77e37c" />
<img width="680" height="508" alt="image" src="https://github.com/user-attachments/assets/a5b5e3e8-d1ba-4d46-9d3b-69cd49a3e1cd" />
<img width="780" height="512" alt="image" src="https://github.com/user-attachments/assets/26a03dfa-6920-4084-8ff2-02573e754ff1" />
<img width="651" height="513" alt="image" src="https://github.com/user-attachments/assets/58adcac2-078a-4148-a5f9-42ff02dee1a6" />
<img width="646" height="507" alt="image" src="https://github.com/user-attachments/assets/424990c9-f4c2-4ebb-8c3b-ae904dc2a62a" />
....
<img width="690" height="513" alt="image" src="https://github.com/user-attachments/assets/425941a3-0343-489d-a360-0cfba9008526" />

BÀI 2 : KNN
1. Cách chạy chương trình
   Bước 1: Mở file tại colab.
   Bước 2: chạy file.
2.Thông số động (Dynamic Input)Chương trình cho phép cấu hình tham số mô hình và dữ liệu kiểm thử:
  Nhập giá trị K: Số lượng hàng xóm cần xét (Ví dụ: 3, 5, 7). Code có thiết lập giới hạn K_LIMIT = 11 để tránh việc chọn K quá lớn gây mất tính cục bộ.
  Nhập tọa độ điểm mới: Người dùng nhập tọa độ $X$ và $Y$ cho một điểm dữ liệu bất kỳ trên mặt phẳng để máy tính dự đoán xem điểm đó thuộc lớp (màu) nào.
3. Giải thích thuật toán & CodeTôi sử dụng thuật toán k-NN (Học có giám sát) theo phương pháp "Học lười" (Lazy Learning).
   Nguyên lý: "Gần mực thì đen, gần đèn thì rạng". Một điểm dữ liệu mới sẽ có xu hướng thuộc về cùng một nhóm với các điểm nằm gần nó nhất.
   Hàm PhanLoai_KNN (Thủ công):Tính khoảng cách:
     Tính khoảng cách Euclidean $\sqrt{\sum (x_i - y_i)^2}$ từ điểm mới đến tất cả các điểm trong tập huấn luyện.
     Tìm láng giềng: Sắp xếp khoảng cách từ bé đến lớn và lấy ra $K$ điểm đầu tiên (Top-K neighbors).
     Bầu chọn đa số (Voting): Đếm xem trong $K$ hàng xóm đó, lớp nào xuất hiện nhiều nhất thì gán nhãn đó cho điểm mới.
   Trực quan hóa:Vẽ các đường nối (nét đứt) từ điểm mới đến $K$ hàng xóm gần nhất để minh họa lý do tại sao máy tính lại đưa ra dự đoán đó.
5. Demo kết quả
<img width="788" height="775" alt="image" src="https://github.com/user-attachments/assets/ef317dad-28b7-47b4-832e-63aa404aece4" />










