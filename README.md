
### 🔧 **Hook trong lập trình là gì?**

**Hook** là một điểm trong chương trình cho phép bạn **chèn (inject) code của riêng mình** để mở rộng hoặc thay đổi hành vi mặc định của hệ thống. Nói cách khác, nó là một **"điểm móc"** nơi bạn có thể **can thiệp** trước, trong hoặc sau một hành động đã được xác định.

**Hành vi mặc định của hệ thống là gì?**

Hành vi mặc định là những gì hệ thống thực hiện một cách tự động khi không có bất kỳ sự can thiệp hay cấu hình tùy chỉnh nào từ phía người dùng hoặc lập trình viên.

📌 Nói cách khác, đó là cách mà một chương trình, framework hoặc component vận hành theo thiết kế ban đầu nếu bạn không thay đổi, ghi đè hay can thiệp gì vào nó.

---

### 🧠 **Tóm tắt các ý chính:**

- 🔄 **Hook là cơ chế mở rộng (extension point)**: Cho phép bạn thêm hoặc thay đổi hành vi của chương trình mà không sửa đổi mã nguồn gốc.
- 🧩 **Thường được cài đặt qua callback**: Một hook có thể sử dụng callback để thực thi đoạn mã tùy chỉnh khi một sự kiện cụ thể xảy ra.
- ⚙️ **Có thể được gọi trước, sau hoặc thay thế logic hiện tại** (e.g., chèn Captcha trước khi login).
- 🕹 **Ứng dụng trong hệ thống plugin**: Ví dụ, trong CMS (như Drupal, WordPress) bạn có thể tạo "hook_user_login()" để xử lý khi người dùng đăng nhập.
- 🕸 **Không chỉ là callback hay event listener**:
  - **Callback**: Là một hàm được truyền như đối số và được gọi để tiếp tục xử lý.
  - **Event Listener**: Lắng nghe sự kiện xảy ra nhiều lần.
  - **Hook**: Có thể giống callback nhưng mang nghĩa mở rộng hệ thống, đôi khi chỉ cần đặt tên hàm đúng để hệ thống tự gọi (magic naming).
- 🧪 **Ví dụ đơn giản trong Python**:
  ```python
  def complicated_func(lst, hook_modify_element, hook_if_negative=None):
      res = sum(hook_modify_element(x) for x in lst)
      if res < 0 and hook_if_negative is not None:
          return hook_if_negative
      return res
  ```

---

### 📌 **Ví dụ trong thực tế:**
- **React**: `useEffect`, `useState` gọi là hooks – cho phép truy cập logic React trong function component.
- **Drupal**: `hook_node_insert()` – được gọi mỗi khi node được insert.
- **Game Mods**: Hook vào các sự kiện như khởi động game, load map, v.v.

---

### 🛡 Lưu ý:
- Hook mạnh mẽ nhưng nếu dùng sai có thể gây **bất ổn hệ thống**.
- Một số hook rất thấp (low-level), như **Windows API hook** cho phép theo dõi hoặc chặn sự kiện hệ thống – thường dùng trong keylogger, screen overlay...

## 🔄 **Hook trong Angular là gì?**

Trong Angular, **hook** là những **phương thức vòng đời (lifecycle methods)** mà bạn có thể **ghi đè (implement)** để chèn logic tại các thời điểm cụ thể trong vòng đời của component, directive hoặc service.

---

## 🧩 **Một số Lifecycle Hooks phổ biến trong Angular**

| Hook | Thời điểm được gọi | Mục đích |
|------|--------------------|----------|
| `ngOnInit()` | Sau khi component khởi tạo | Khởi tạo dữ liệu ban đầu |
| `ngOnChanges()` | Khi input property thay đổi | Theo dõi biến đầu vào |
| `ngDoCheck()` | Tùy chỉnh kiểm tra thay đổi | Hiếm khi dùng |
| `ngAfterViewInit()` | Sau khi view và child view render xong | Thường dùng để xử lý DOM hoặc gọi thư viện UI |
| `ngOnDestroy()` | Trước khi component bị hủy | Dọn dẹp tài nguyên (unsubscribe, remove event, etc.) |

---

## ✅ **Ví dụ sử dụng Hook trong Angular**

```ts
import { Component, OnInit, OnDestroy } from '@angular/core';

@Component({
  selector: 'app-example',
  template: `<p>Example Component</p>`
})
export class ExampleComponent implements OnInit, OnDestroy {
  private intervalId: any;

  // Hook: chạy sau khi component được khởi tạo
  ngOnInit(): void {
    console.log('Component initialized');
    this.intervalId = setInterval(() => {
      console.log('Running every second...');
    }, 1000);
  }

  // Hook: chạy trước khi component bị hủy
  ngOnDestroy(): void {
    console.log('Component destroyed');
    clearInterval(this.intervalId); // Dọn dẹp tài nguyên
  }
}
```

---

## 🧠 **Giải thích:**
- `ngOnInit()` là một hook – bạn **gắn thêm logic** vào thời điểm component đã được Angular khởi tạo.
- `ngOnDestroy()` là một hook – bạn **xử lý dọn dẹp** khi component bị tháo khỏi DOM.

---

## 📌 Ngoài Component, hook cũng dùng trong:
- **Directive** (e.g., `ngAfterViewInit` trong directive DOM)
- **Service** (khi dùng `Injectable` + `OnDestroy`)
- **Custom Form Controls** với `ControlValueAccessor` cũng có các hook đặc biệt như `registerOnChange`, `registerOnTouched`.


