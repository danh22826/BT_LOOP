    Start((Bắt đầu)) --> LoadData[Load dữ liệu từ CSV\nmovies, showtimes, seats]
    LoadData --> HienMenu[Hiển thị Menu Chính]
    
    HienMenu -->|Chọn Đặt vé| ChonPhim[Khách chọn Phim]
    ChonPhim --> TimSuat[Hệ thống tìm các Suất chiếu\ncủa phim đó]
    
    TimSuat -->|Hiển thị DS| ChonSuat[Khách chọn Suất chiếu]
    
    ChonSuat --> CheckGhe{Kiểm tra ghế}
    
    CheckGhe -->|Gọi datveo.cpp| HienGheTrong[Hiển thị sơ đồ ghế\ndisplayAvailableSeats]
    HienGheTrong --> NhapGhe[Khách nhập vị trí ghế\nVí dụ: A5]
    
    NhapGhe --> KiemTraGhe{Ghế có trống không?\ncheckSeatAvailable}
    
    KiemTraGhe -- Không --> BaoLoi[Báo lỗi: Ghế đã đặt]
    BaoLoi --> HienGheTrong
    
    KiemTraGhe -- Có --> KhoaGhe[Tạm khóa ghế\noccupySeat]
    KhoaGhe --> ThanhToan[Xử lý thanh toán]
    
    ThanhToan --> TaoVe[Tạo đối tượng Ticket\nLưu vào tickets.csv]
    TaoVe --> UpdateSeat[Cập nhật trạng thái ghế\nvào showtimes.csv]
    
    UpdateSeat --> InVe[In vé ra màn hình]
    InVe --> End((Kết thúc))
