Để tạo một block trong Drupal 10 bằng cách sử dụng giao diện người dùng, bạn có thể thực hiện theo các bước sau:

### Bước 1: Tạo Custom Block Type

1. Đăng nhập vào trang quản trị Drupal của bạn.
2. Điều hướng đến **Structure** (Cấu trúc) -> **Block layout** (Bố cục khối).
3. Nhấp vào tab **Custom block library** (Thư viện khối tùy chỉnh).
4. Nhấp vào **+ Add custom block type** (Thêm loại khối tùy chỉnh).
5. Đặt tên cho loại khối mới của bạn, ví dụ: `My Custom Block`. Sau đó nhấp vào **Save** (Lưu).

### Bước 2: Thêm các trường cho Custom Block Type

1. Sau khi tạo loại khối tùy chỉnh, nhấp vào **Manage fields** (Quản lý trường) bên cạnh loại khối vừa tạo.
2. Nhấp vào **+ Add field** (Thêm trường).
3. Chọn **Add a new field** (Thêm một trường mới) và chọn **Text (plain)** cho trường `title`.
4. Đặt **Label** (Nhãn) là `Title` và nhấp vào **Save and continue** (Lưu và tiếp tục).
5. Nhấp vào **Save field settings** (Lưu cài đặt trường) mà không cần thay đổi gì thêm.
6. Lặp lại các bước trên để tạo các trường `Subtitle`, `Content`, và `Image`:
   - `Subtitle`: **Text (plain)**
   - `Content`: **Text (formatted, long, with summary)** (Văn bản có định dạng, dài, với tóm tắt)
   - `Image`: **Image** (Hình ảnh)

### Bước 3: Tạo một Custom Block

1. Quay lại **Structure** (Cấu trúc) -> **Block layout** (Bố cục khối).
2. Nhấp vào tab **Custom block library** (Thư viện khối tùy chỉnh).
3. Nhấp vào **+ Add custom block** (Thêm khối tùy chỉnh).
4. Chọn loại khối vừa tạo (`My Custom Block`).
5. Điền thông tin cho các trường `Title`, `Subtitle`, `Content`, và tải lên `Image`.
6. Nhấp vào **Save** (Lưu).

### Bước 4: Đặt Custom Block vào Block Layout

1. Quay lại **Structure** (Cấu trúc) -> **Block layout** (Bố cục khối).
2. Tìm vùng mà bạn muốn đặt block mới tạo.
3. Nhấp vào **Place block** (Đặt khối) bên cạnh vùng bạn muốn thêm block.
4. Chọn khối bạn vừa tạo từ danh sách và nhấp vào **Place block**.
5. Đặt cấu hình hiển thị nếu cần và nhấp vào **Save block** (Lưu khối).

### Bước 5: Tùy chỉnh giao diện (Theme)

Nếu bạn muốn tùy chỉnh giao diện hiển thị của block, bạn có thể tạo một template file trong theme của bạn.

1. Điều hướng đến thư mục theme của bạn, ví dụ: `themes/custom/your_theme/templates/`.
2. Tạo một file template cho block, ví dụ: `block--my-custom-block.html.twig`.
3. Thêm nội dung vào file template:

```html
<div class="my-custom-block">
  <div class="row">
    <div class="col-6">
<img src="{{ content.field_image[0]['#item'].entity.uri.value }}" alt="{{ content.field_title[0]['#markup'] }}" class="img-fluid">
    </div>
    <div class="col-12 col-md-6">
      <h2>{{ content.field_title[0]['#markup'] }}</h2>
      <h3>{{ content.field_subtitle[0]['#markup'] }}</h3>
      <div>{{ content.field_content[0]['#markup'] }}</div>
    </div>
  </div>
</div>
```

4. Xóa cache của Drupal để áp dụng template mới:

```sh
drush cr
```

Bây giờ, block của bạn sẽ hiển thị với cấu trúc và định dạng mà bạn đã định nghĩa trong template.
