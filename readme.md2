Để tạo một block sử dụng Views trong Drupal 10 và render các trường `title`, `subtitle`, `content`, và `image`, bạn có thể làm theo các bước sau:

### Bước 1: Tạo Custom Content Type

1. Đăng nhập vào trang quản trị Drupal của bạn.
2. Điều hướng đến **Structure** (Cấu trúc) -> **Content types** (Loại nội dung).
3. Nhấp vào **+ Add content type** (Thêm loại nội dung).
4. Đặt tên cho loại nội dung mới của bạn, ví dụ: `My Custom Content`. Sau đó nhấp vào **Save and manage fields** (Lưu và quản lý trường).

### Bước 2: Thêm các trường cho Content Type

1. Nhấp vào **+ Add field** (Thêm trường).
2. Chọn **Add a new field** (Thêm một trường mới) và chọn **Text (plain)** cho trường `title`.
3. Đặt **Label** (Nhãn) là `Title` và nhấp vào **Save and continue** (Lưu và tiếp tục).
4. Nhấp vào **Save field settings** (Lưu cài đặt trường) mà không cần thay đổi gì thêm.
5. Lặp lại các bước trên để tạo các trường `Subtitle`, `Content`, và `Image`:
   - `Subtitle`: **Text (plain)**
   - `Content`: **Text (formatted, long, with summary)** (Văn bản có định dạng, dài, với tóm tắt)
   - `Image`: **Image** (Hình ảnh)

### Bước 3: Tạo một Custom View

1. Điều hướng đến **Structure** (Cấu trúc) -> **Views**.
2. Nhấp vào **+ Add view** (Thêm view).
3. Đặt tên cho view, ví dụ: `My Custom Block View`.
4. Chọn hiển thị nội dung của loại `My Custom Content`.
5. Chọn `Create a block` (Tạo một block) và nhấp vào **Save and edit** (Lưu và chỉnh sửa).

### Bước 4: Cấu hình View để Hiển thị Các Trường

1. Trong giao diện chỉnh sửa view, nhấp vào **Add** bên cạnh **Fields** (Các trường).
2. Thêm các trường `Title`, `Subtitle`, `Content`, và `Image`.
3. Đối với mỗi trường:
   - `Title`: Để nguyên thiết lập mặc định.
   - `Subtitle`: Để nguyên thiết lập mặc định.
   - `Content`: Để nguyên thiết lập mặc định.
   - `Image`: Trong mục **Format** (Định dạng), chọn **Image Style** (Kiểu ảnh) và chọn kiểu ảnh phù hợp (ví dụ: thumbnail).

4. Sắp xếp các trường theo thứ tự mong muốn.
5. Nhấp vào **Save** (Lưu).

### Bước 5: Đặt Block vào Layout

1. Điều hướng đến **Structure** (Cấu trúc) -> **Block layout** (Bố cục khối).
2. Tìm vùng mà bạn muốn đặt block mới tạo.
3. Nhấp vào **Place block** (Đặt khối) bên cạnh vùng bạn muốn thêm block.
4. Chọn block view bạn vừa tạo từ danh sách và nhấp vào **Place block**.
5. Đặt cấu hình hiển thị nếu cần và nhấp vào **Save block** (Lưu khối).

### Bước 6: Tùy chỉnh Giao diện (Theme)

Nếu bạn muốn tùy chỉnh giao diện hiển thị của block, bạn có thể tạo một template file trong theme của bạn.
1. Điều hướng đến thư mục theme của bạn, ví dụ: `themes/custom/your_theme/templates/views-view-unformatted--my-custom-block-view.html.twig`.
2. Thêm nội dung vào file template:

```html
<div class="my-custom-block">
  {% for row in rows %}
    <div class="row">
      <div class="col-6">
        {{ row.content['field_image'] }}
      </div>
      <div class="col-12 col-md-6">
        <h2>{{ row.content['title'] }}</h2>
        <h3>{{ row.content['subtitle'] }}</h3>
        <div>{{ row.content['content'] }}</div>
      </div>
    </div>
  {% endfor %}
</div>
```

3. Xóa cache của Drupal để áp dụng template mới:

```sh
drush cr
```

Bây giờ, block của bạn sẽ hiển thị với cấu trúc và định dạng mà bạn đã định nghĩa trong template.
<div class="my-custom-block">
  {% set count = 0 %}
  <div class="row">
  {% for row in rows %}
    <div class="col-6">
      {{ row.content['field_image'] }}
      <h2>{{ row.content['title'] }}</h2>
      <h3>{{ row.content['subtitle'] }}</h3>
      <div>{{ row.content['content'] }}</div>
    </div>
    {% set count = count + 1 %}
    {% if count % 2 == 0 and not loop.last %}
      </div><div class="row">
    {% endif %}
  {% endfor %}
  </div>
</div>
