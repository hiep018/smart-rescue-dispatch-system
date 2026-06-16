Dưới đây là nội dung Markdown thuần được trích xuất và tổng hợp lại từ file JSON (Jupyter Notebook) bạn vừa gửi. Bạn có thể copy toàn bộ nội dung này để sử dụng trực tiếp cho file README.md của mình:🚨 Hệ Thống Điều Phối Cứu Hộ Thông MinhDự án được xây dựng bằng Python Django, hỗ trợ tiếp nhận yêu cầu cứu hộ, xác định vị trí người gặp nạn và lựa chọn trạm cứu hộ phù hợp.Hệ thống sử dụng GPS, Leaflet, OpenStreetMap, địa chỉ ô 3 từ, thuật toán A* và dịch vụ OSRM để tính toán quãng đường, thời gian di chuyển và hiển thị tuyến đường cứu hộ trên bản đồ.✨ Chức năng chínhXác định vị trí: Lấy vị trí bằng GPS, chọn trực tiếp trên bản đồ hoặc nhập địa chỉ ô 3 từ.Gửi yêu cầu cứu hộ: Lưu tên người gặp nạn, số điện thoại, mức độ khẩn cấp và mô tả sự cố.Quản lý trạm cứu hộ: Quản lý vị trí, trạng thái và số lượng phương tiện của từng trạm.Điều phối thông minh: Sử dụng thuật toán A* kết hợp OSRM để lựa chọn trạm cứu hộ phù hợp.Hiển thị tuyến đường: Hiển thị vị trí trạm, vị trí người gặp nạn và tuyến đường cứu hộ trên bản đồ.Theo dõi trạng thái: Theo dõi yêu cầu từ lúc chờ tiếp nhận đến khi hoàn thành hoặc hủy.Thống kê hệ thống: Thống kê số trạm, số yêu cầu đang xử lý và số yêu cầu đã hoàn thành.🛠 Yêu cầu phần cứng và phần mềmHệ điều hành: Windows 10/11CPU: Intel Core i3 trở lên hoặc tương đươngRAM: Tối thiểu 4 GBPython: 3.10 – 3.12, khuyến nghị Python 3.12Editor: Visual Studio CodeTrình duyệt: Google Chrome hoặc Microsoft EdgeKết nối Internet: Cần thiết để tải bản đồ và sử dụng dịch vụ OSRMGit: Dùng để tải và cập nhật mã nguồnHệ thống cứu hộ không cần cài OpenCV, InsightFace, ONNX Runtime, CUDA hoặc GPU NVIDIA.⚙️ Hướng dẫn cài đặt môi trườngBước 1: Pull dự án về máyMở Terminal trong Visual Studio Code và chạy:Bashgit pull
Nếu máy chưa có dự án, sử dụng:Bashgit clone <đường-dẫn-repository>
Sau đó mở thư mục dự án vừa tải về.Bước 2: Di chuyển đến thư mục chứa manage.pyBashcd django_app
Nếu Terminal đã đứng tại thư mục chứa manage.py thì không cần chạy lệnh này.Bước 3: Tạo môi trường ảoChỉ cần thực hiện trong lần cài đặt đầu tiên:Bashpython -m venv venv
Bước 4: Kích hoạt môi trường ảoTrên Windows:Bashvenv\Scripts\activate
Nếu sử dụng PowerShell và bị chặn quyền chạy:PowerShellSet-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
venv\Scripts\Activate.ps1
Bước 5: Nâng cấp pipBashpython -m pip install --upgrade pip
Bước 6: Cài đặt các thư viện cần thiếtBashpip install Django Pillow python-dotenv
Kiểm tra Django đã được cài thành công:Bashpython -m django --version
Bước 7: Cập nhật cơ sở dữ liệuBashpython manage.py migrate
Chỉ khi có chỉnh sửa cấu trúc trong file models.py, chạy:Bashpython manage.py makemigrations
python manage.py migrate
Khi chỉ git pull dự án về và đã có sẵn migration thì không cần chạy makemigrations.Bước 8: Tạo dữ liệu cứu hộ mẫuBước này không bắt buộc. Chỉ chạy khi cần dữ liệu để kiểm thử hoặc trình diễn:Bashpython manage.py create_demo_rescue_data
Lệnh trên sẽ tạo:Các trạm cứu hộ mẫu.Các yêu cầu cứu hộ mẫu.Vị trí và trạng thái ban đầu để kiểm thử hệ thống.📁 Cấu trúc thư mụcPlaintextdjango_app/
├── manage.py
├── db.sqlite3
├── requirements.txt
├── README.md
│
├── attendance_system/
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   ├── asgi.py
│   └── wsgi.py
│
├── portal/
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── models.py
│   ├── views.py
│   ├── urls.py
│   ├── auto_dispatch.py
│   ├── custom_map_views.py
│   ├── what3words_views.py
│   │
│   ├── migrations/
│   │   └── ...
│   │
│   └── management/
│       ├── __init__.py
│       └── commands/
│           ├── __init__.py
│           └── create_demo_rescue_data.py
│
├── templates/
│   ├── base.html
│   └── portal/
│       ├── home.html
│       ├── admin_dashboard.html
│       └── rescue_map.html
│
└── static/
    ├── css/
    ├── js/
    └── images/
🚀 Cách sử dụngBước 1: Kích hoạt môi trường ảoBashvenv\Scripts\activate
Bước 2: Cập nhật mã nguồn mới nhấtBashgit pull
Bước 3: Cập nhật cơ sở dữ liệuBashpython manage.py migrate
Bước 4: Khởi chạy chương trìnhBashpython manage.py runserver
Sau khi server chạy thành công, Terminal sẽ hiển thị:PlaintextStarting development server at http://127.0.0.1:8000/
🌐 Các địa chỉ truy cậpTrang gửi yêu cầu cứu hộPlaintexthttp://127.0.0.1:8000/
Trung tâm điều phốiPlaintexthttp://127.0.0.1:8000/admin-dashboard/
Bản đồ điều phối cứu hộPlaintexthttp://127.0.0.1:8000/rescue-map/
Trang quản trị DjangoPlaintexthttp://127.0.0.1:8000/admin/
🧭 Quy trình hoạt độngNgười dùng truy cập trang gửi yêu cầu cứu hộ.Người dùng xác định vị trí bằng một trong ba cách:Lấy vị trí GPS.Chọn trực tiếp trên bản đồ.Nhập địa chỉ ô 3 từ.Người dùng nhập thông tin cá nhân và mô tả sự cố.Yêu cầu được lưu ở trạng thái pending.Điều phối viên truy cập trung tâm điều phối.Điều phối viên nhấn nút Điều phối A*.Hệ thống kiểm tra các trạm còn phương tiện.OSRM tính quãng đường và thời gian di chuyển thực tế.Hệ thống lựa chọn trạm phù hợp.Tuyến đường cứu hộ được hiển thị trên bản đồ.Điều phối viên cập nhật trạng thái yêu cầu đến khi hoàn thành.📌 Trạng thái yêu cầu cứu hộTrạng tháiÝ nghĩapendingĐang chờ tiếp nhậnassignedĐã phân công trạmon_the_wayĐang trên đường cứu hộcompletedĐã hoàn thànhcancelledĐã hủy🚑 Trạng thái trạm cứu hộTrạng tháiÝ nghĩaavailableTrạm đang sẵn sàngbusyTrạm đã sử dụng hết phương tiệninactiveTrạm tạm ngừng hoạt độngSố phương tiện còn trống được tính theo công thức:PlaintextSố xe còn trống = Tổng số xe - Số yêu cầu đang thực hiện
✅ Kiểm tra hệ thống hoạt độngKiểm tra cấu hình Django:Bashpython manage.py check
Kết quả mong đợi:PlaintextSystem check identified no issues (0 silenced).
Kiểm tra danh sách trạm cứu hộ:Plaintexthttp://127.0.0.1:8000/api/rescue-stations/
Kiểm tra thống kê hệ thống:Plaintexthttp://127.0.0.1:8000/api/stats/
Kiểm tra dữ liệu bản đồ:Plaintexthttp://127.0.0.1:8000/api/custom-map/data/
🔁 Các lệnh sử dụng trong những lần chạy sauBashvenv\Scripts\activate
git pull
python manage.py migrate
python manage.py runserver
Nếu không cần cập nhật mã nguồn từ Git, có thể bỏ qua:Bashgit pull
⏹ Dừng chương trìnhTại Terminal đang chạy Django Server, nhấn:PlaintextCtrl + C
Thoát môi trường ảo:Bashdeactivate
📝 Lưu ý khi đưa dự án lên GitKhông nên push các file và thư mục sau:Plaintextvenv/
__pycache__/
*.pyc
.env
.vscode/
.idea/
db.sqlite3
Cần push các thành phần sau:Plaintextmanage.py
requirements.txt
attendance_system/
portal/
portal/migrations/
portal/management/commands/
templates/
static/
README.md
Sau khi thành viên trong nhóm clone dự án, chỉ cần chạy:Bashpython manage.py migrate
python manage.py create_demo_rescue_data
python manage.py runserver
