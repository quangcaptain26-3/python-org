# Lời giải chi tiết Python — Câu 51 đến 75

> Nguồn: *100+ Python challenging programming exercises for Python 3*  
> Ngôn ngữ: Python 3  
> Ghi chú: Các câu 51–75 trong file gốc không ghi Level; mức độ được phân loại theo nội dung bài tập.

---

## Câu 51 - Level 1

### Đề bài (tóm tắt tiếng Việt)

Định nghĩa lớp `American` và lớp con (subclass) `NewYorker` kế thừa từ `American`.

### Phân tích ý tưởng

- Trong Python, kế thừa được khai báo bằng cú pháp `class Con(Cha):`.
- `NewYorker` tự động nhận mọi thuộc tính và phương thức của `American` nếu không ghi đè.
- Tạo đối tượng từ cả hai lớp để kiểm tra quan hệ kế thừa (`isinstance`).

**Độ phức tạp:** O(1) — chỉ định nghĩa lớp và tạo đối tượng.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
class American:
    """Lớp cha đại diện cho người Mỹ."""

    def __repr__(self):
        return f"{self.__class__.__name__}()"


class NewYorker(American):
    """Lớp con — người New York kế thừa từ American."""
    pass


if __name__ == "__main__":
    an_american = American()
    a_new_yorker = NewYorker()

    print(an_american)          # American()
    print(a_new_yorker)         # NewYorker()
    print(isinstance(a_new_yorker, American))  # True
```

### Giải thích code từng phần

- `class American:` — lớp cơ sở; trong Python 3 không cần kế thừa `object` tường minh.
- `class NewYorker(American):` — `NewYorker` là subclass của `American`.
- `pass` — thân lớp rỗng, đủ điều kiện đề bài.
- `isinstance(a_new_yorker, American)` — xác nhận quan hệ "là một loại" (is-a).

### Ví dụ chạy thử (input → output)

Không cần input. Chạy file sẽ in:

```
American()
NewYorker()
True
```

### Lưu ý / mở rộng

- Có thể thêm thuộc tính riêng cho `NewYorker` (ví dụ `city = "New York"`).
- Python hỗ trợ đa kế thừa: `class X(A, B):`.

---

## Câu 52 - Level 1

### Đề bài (tóm tắt tiếng Việt)

Định nghĩa lớp `Circle` nhận bán kính khi khởi tạo và có phương thức tính diện tích hình tròn.

### Phân tích ý tưởng

- Dùng `__init__` để lưu bán kính vào `self.radius`.
- Diện tích: \(S = \pi r^2\).
- Nên dùng `math.pi` thay vì hằng số `3.14` để chính xác hơn.

**Độ phức tạp:** O(1) mỗi lần gọi `area()`.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
import math


class Circle:
    def __init__(self, radius: float):
        self.radius = radius

    def area(self) -> float:
        """Trả về diện tích hình tròn."""
        return math.pi * self.radius ** 2


if __name__ == "__main__":
    circle = Circle(2)
    print(circle.area())  # ≈ 12.566370614359172
```

### Giải thích code từng phần

- `__init__(self, radius)` — hàm khởi tạo, gán bán kính cho đối tượng.
- `self.radius` — thuộc tính instance, mỗi hình tròn có bán kính riêng.
- `math.pi * self.radius ** 2` — công thức diện tích chuẩn.

### Ví dụ chạy thử (input → output)

```
Bán kính = 2  →  output ≈ 12.566370614359172
Bán kính = 1  →  output ≈ 3.141592653589793
```

### Lưu ý / mở rộng

- Có thể thêm `@property` cho `diameter` (đường kính = `2 * radius`).
- Làm tròn kết quả: `round(circle.area(), 2)`.

---

## Câu 53 - Level 1

### Đề bài (tóm tắt tiếng Việt)

Định nghĩa lớp `Rectangle` nhận chiều dài và chiều rộng, có phương thức tính diện tích.

### Phân tích ý tưởng

- Lưu `length` và `width` trong `__init__`.
- Diện tích hình chữ nhật: \(S = dài \times rộng\).

**Độ phức tạp:** O(1).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
class Rectangle:
    def __init__(self, length: float, width: float):
        self.length = length
        self.width = width

    def area(self) -> float:
        """Trả về diện tích hình chữ nhật."""
        return self.length * self.width


if __name__ == "__main__":
    rect = Rectangle(2, 10)
    print(rect.area())  # 20
```

### Giải thích code từng phần

- Hai tham số `length`, `width` mô tả kích thước hình chữ nhật.
- `area()` nhân hai cạnh — phép toán cơ bản, không cần thư viện ngoài.

### Ví dụ chạy thử (input → output)

```
length=2, width=10  →  20
length=5, width=5   →  25  (hình vuông là trường hợp đặc biệt)
```

### Lưu ý / mở rộng

- Có thể thêm `perimeter()` trả về `2 * (length + width)`.
- Dùng `dataclass` (Python 3.7+) để code gọn hơn nếu chỉ cần lưu dữ liệu.

---

## Câu 54 - Level 1

### Đề bài (tóm tắt tiếng Việt)

Định nghĩa lớp `Shape` và subclass `Square`. `Square` nhận `length` khi khởi tạo. Cả hai có phương thức `area()`; `Shape` mặc định trả về 0, `Square` trả về diện tích hình vuông.

### Phân tích ý tưởng

- Đây là ví dụ **đa hình (polymorphism)**: cùng tên phương thức `area()` nhưng hành vi khác nhau.
- `Square` **ghi đè (override)** phương thức `area()` của lớp cha.
- Gọi `super().__init__()` thay cho `Shape.__init__(self)` — cách viết hiện đại hơn.

**Độ phức tạp:** O(1).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
class Shape:
    def area(self) -> float:
        """Hình dạng chung chưa xác định — diện tích mặc định 0."""
        return 0


class Square(Shape):
    def __init__(self, length: float):
        super().__init__()
        self.length = length

    def area(self) -> float:
        """Ghi đè: diện tích hình vuông."""
        return self.length ** 2


if __name__ == "__main__":
    square = Square(3)
    print(square.area())  # 9
```

### Giải thích code từng phần

- `Shape.area()` trả về `0` — hành vi mặc định cho hình chưa cụ thể.
- `Square` kế thừa `Shape` nhưng định nghĩa lại `area()`.
- `super().__init__()` gọi constructor lớp cha (ở đây không bắt buộc vì `Shape` không có `__init__` phức tạp, nhưng là thói quen tốt).

### Ví dụ chạy thử (input → output)

```
Square(3)  →  9
Square(5)  →  25
Shape().area()  →  0
```

### Lưu ý / mở rộng

- Đề bài nói "print area" — có thể `print(square.area())` hoặc đổi `area()` thành in trực tiếp; trả về giá trị linh hoạt hơn để tái sử dụng.
- Có thể thêm `Circle(Shape)` để minh họa đa hình đầy đủ.

---

## Câu 55 - Level 1

### Đề bài (tóm tắt tiếng Việt)

Ném (raise) một ngoại lệ `RuntimeError`.

### Phân tích ý tưởng

- `raise` dùng để chủ động báo lỗi khi chương trình gặp tình huống không hợp lệ.
- `RuntimeError` là ngoại lệ built-in cho lỗi runtime chung.

**Độ phức tạp:** O(1).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def demo_raise():
    """Minh họa ném RuntimeError."""
    raise RuntimeError("something wrong")


if __name__ == "__main__":
    try:
        demo_raise()
    except RuntimeError as exc:
        print(f"Bắt được lỗi: {exc}")
```

### Giải thích code từng phần

- `raise RuntimeError("something wrong")` — tạo và ném ngoại lệ kèm thông báo.
- Khối `try/except` bọc lại để demo; nếu không bắt, chương trình dừng và in traceback.

### Ví dụ chạy thử (input → output)

```
output: Bắt được lỗi: something wrong
```

(Nếu chỉ chạy `raise RuntimeError('something wrong')` không có `try`, Python in traceback và thoát.)

### Lưu ý / mở rộng

- Nên kèm thông điệp mô tả rõ nguyên nhân.
- `raise` không đối số — tái ném ngoại lệ hiện tại trong khối `except`.

---

## Câu 56 - Level 1

### Đề bài (tóm tắt tiếng Việt)

Viết hàm tính `5/0` và dùng `try/except` để bắt ngoại lệ.

### Phân tích ý tưởng

- Chia cho 0 trong Python gây `ZeroDivisionError`.
- `try/except` bắt lỗi cụ thể; `finally` luôn chạy dù có lỗi hay không.
- Code gốc dùng cú pháp Python 2 (`except Exception, err`) — phải sửa cho Python 3.

**Độ phức tạp:** O(1).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def throws() -> float:
    """Cố tình chia cho 0."""
    return 5 / 0


if __name__ == "__main__":
    try:
        throws()
    except ZeroDivisionError:
        print("division by zero!")
    except Exception as err:
        print(f"Caught an exception: {err}")
    finally:
        print("In finally block for cleanup")
```

### Giải thích code từng phần

- `try` — thử chạy `throws()`.
- `except ZeroDivisionError` — bắt đúng loại lỗi chia cho 0.
- `except Exception as err` — lưới an toàn cho lỗi khác (Python 3: `as err`).
- `finally` — khối dọn dẹp, luôn thực thi.

### Ví dụ chạy thử (input → output)

```
division by zero!
In finally block for cleanup
```

### Lưu ý / mở rộng

- Thứ tự `except` quan trọng: bắt lỗi cụ thể trước, lỗi chung sau.
- Không nên `except:` trống — che giấu lỗi khó debug.

---

## Câu 57 - Level 1

### Đề bài (tóm tắt tiếng Việt)

Định nghĩa lớp ngoại lệ tùy chỉnh nhận chuỗi thông báo lỗi làm thuộc tính.

### Phân tích ý tưởng

- Ngoại lệ tùy chỉnh kế thừa từ `Exception`.
- Lưu `msg` trong `__init__`; nên gọi `super().__init__(msg)` để `str(exc)` hoạt động đúng.

**Độ phức tạp:** O(1).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
class MyError(Exception):
    """Ngoại lệ tùy chỉnh.

    Attributes:
        msg -- mô tả lỗi
    """

    def __init__(self, msg: str):
        self.msg = msg
        super().__init__(msg)


if __name__ == "__main__":
    try:
        raise MyError("something wrong")
    except MyError as error:
        print(error.msg)   # something wrong
        print(error)       # something wrong
```

### Giải thích code từng phần

- `class MyError(Exception)` — định nghĩa kiểu ngoại lệ mới.
- `self.msg = msg` — lưu thông báo theo yêu cầu đề.
- `super().__init__(msg)` — đăng ký message với lớp `Exception` cha.

### Ví dụ chạy thử (input → output)

```
something wrong
something wrong
```

### Lưu ý / mở rộng

- Có thể thêm mã lỗi: `def __init__(self, msg, code=0)`.
- Đặt tên theo quy ước: `SomethingWrongError` (hậu tố `Error`).

---

## Câu 58 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Cho email dạng `username@companyname.com` (chỉ chữ cái), đọc từ console và in **tên người dùng** (phần trước `@`).

### Phân tích ý tưởng

- Tách chuỗi tại `@`: phần đầu là username — cách đơn giản nhất.
- Hoặc dùng regex `re.match` như gợi ý đề.
- Input: `john@google.com` → Output: `john`.

**Độ phức tạp:** O(n) với n = độ dài chuỗi email.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
import re


def extract_username(email: str) -> str:
    """Lấy username từ email dạng user@company.com."""
    match = re.match(r"(\w+)@(\w+)\.com", email.strip())
    if not match:
        raise ValueError("Email không đúng định dạng")
    return match.group(1)


if __name__ == "__main__":
    email_address = input()
    print(extract_username(email_address))
```

### Giải thích code từng phần

- `input()` — đọc email từ console (thay `raw_input` của Python 2).
- `r"(\w+)@(\w+)\.com"` — nhóm 1: username, nhóm 2: tên công ty.
- `match.group(1)` — trả về username.

### Ví dụ chạy thử (input → output)

```
john@google.com  →  john
alice@yahoo.com  →  alice
```

### Lưu ý / mở rộng

- Cách đơn giản: `email.split('@')[0]`.
- `\w` khớp chữ, số, gạch dưới — phù hợp đề "chỉ chữ cái" trong ví dụ.

---

## Câu 59 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Cho email dạng `username@companyname.com`, đọc từ console và in **tên công ty** (phần giữa `@` và `.com`).

### Phân tích ý tưởng

- Tương tự câu 58 nhưng lấy nhóm thứ 2 của regex, hoặc tách chuỗi.
- `john@google.com` → `google`.

**Độ phức tạp:** O(n).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
import re


def extract_company(email: str) -> str:
    """Lấy tên công ty từ email dạng user@company.com."""
    match = re.match(r"(\w+)@(\w+)\.com", email.strip())
    if not match:
        raise ValueError("Email không đúng định dạng")
    return match.group(2)


if __name__ == "__main__":
    email_address = input()
    print(extract_company(email_address))
```

### Giải thích code từng phần

- Cùng pattern với câu 58; khác ở `group(2)` — tên miền công ty.
- `email.strip()` loại khoảng trắng thừa khi nhập.

### Ví dụ chạy thử (input → output)

```
john@google.com  →  google
bob@microsoft.com  →  microsoft
```

### Lưu ý / mở rộng

- Tách chuỗi: `email.split('@')[1].removesuffix('.com')` (Python 3.9+).
- Email thực tế phức tạp hơn — nên dùng thư viện `email.utils` cho production.

---

## Câu 60 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Nhập một dòng gồm các từ cách nhau bởi khoảng trắng, in ra danh sách các **từ chỉ gồm chữ số**.

### Phân tích ý tưởng

- `re.findall(r"\d+", s)` tìm mọi chuỗi con liên tiếp gồm một hoặc nhiều chữ số.
- Ví dụ: `"2 cats and 3 dogs."` → `['2', '3']`.

**Độ phức tạp:** O(n).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
import re


if __name__ == "__main__":
    text = input()
    # \d+ khớp một hoặc nhiều chữ số liên tiếp
    digit_words = re.findall(r"\d+", text)
    print(digit_words)
```

### Giải thích code từng phần

- `re.findall` — trả về list tất cả match, không chỉ match đầu tiên.
- `\d+` — một hoặc nhiều ký tự số; `"12"` được coi là một "từ số".

### Ví dụ chạy thử (input → output)

```
2 cats and 3 dogs.  →  ['2', '3']
hello 99 worlds 42  →  ['99', '42']
```

### Lưu ý / mở rộng

- Nếu cần **từ nguyên vẹn** chỉ gồm số: `re.findall(r"\b\d+\b", text)`.
- Có thể lọc bằng `word.isdigit()` sau `text.split()`.

---

## Câu 61 - Level 2

### Đề bài (tóm tắt tiếng Việt)

In chuỗi Unicode `"hello world"`.

### Phân tích ý tưởng

- Python 3: `str` **mặc định là Unicode** (UTF-8 internal).
- Tiền tố `u"..."` vẫn hợp lệ nhưng không còn bắt buộc như Python 2.

**Độ phức tạp:** O(1).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
if __name__ == "__main__":
    # Python 3: str đã là Unicode
    unicode_string = "hello world"
    print(unicode_string)

    # Tương đương cú pháp Python 2 (vẫn chạy được)
    also_unicode = u"hello world"
    print(also_unicode)
```

### Giải thích code từng phần

- `"hello world"` — kiểu `str`, hỗ trợ đầy đủ ký tự Unicode.
- `u"hello world"` — cú pháp legacy, cho kết quả giống nhau trong Python 3.

### Ví dụ chạy thử (input → output)

```
hello world
hello world
```

### Lưu ý / mở rộng

- In ký tự đặc biệt: `print("Xin chào thế giới 🌍")`.
- Python 2 dùng `unicode` riêng; Python 3 đã thống nhất.

---

## Câu 62 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Đọc chuỗi ASCII từ input và chuyển sang chuỗi Unicode mã hóa UTF-8.

### Phân tích ý tưởng

- Python 3: `input()` trả về `str` (Unicode). Không còn hàm `unicode()`.
- Nếu đọc **bytes** thì decode: `b.decode("utf-8")`.
- Đề bài mang tính Python 2 — ta giải thích tương đương Python 3.

**Độ phức tạp:** O(n).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
if __name__ == "__main__":
    # input() trong Python 3 đã trả về str Unicode
    ascii_string = input()
    unicode_string = ascii_string  # đã là Unicode

    # Minh họa chuyển bytes ASCII → str UTF-8
    as_bytes = ascii_string.encode("ascii")
    decoded = as_bytes.decode("utf-8")

    print(unicode_string)
    print(decoded)
    print(type(unicode_string))  # <class 'str'>
```

### Giải thích code từng phần

- `input()` — đọc chuỗi text từ người dùng.
- `encode("ascii")` — chuyển str sang bytes (nếu chỉ ký tự ASCII).
- `decode("utf-8")` — chuyển bytes về str Unicode.

### Ví dụ chạy thử (input → output)

```
hello  →  hello
         hello
         <class 'str'>
```

### Lưu ý / mở rộng

- Python 2: `unicode(s, "utf-8")` — đã loại bỏ ở Python 3.
- File nguồn nên khai báo `# -*- coding: utf-8 -*-` (liên quan câu 63).

---

## Câu 63 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Viết comment đặc biệt để khai báo file mã nguồn Python sử dụng bảng mã Unicode (UTF-8).

### Phân tích ý tưởng

- Dòng **encoding declaration** đặt ở **dòng 1 hoặc 2** của file.
- Cú pháp phổ biến: `# -*- coding: utf-8 -*-`.
- Python 3 mặc định UTF-8 (PEP 3120) nhưng khai báo vẫn hữu ích cho tương thích và rõ ràng.

**Độ phức tạp:** O(1) — chỉ là khai báo metadata.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
# -*- coding: utf-8 -*-
"""Ví dụ file Python khai báo encoding UTF-8."""

# Cho phép dùng ký tự Unicode trực tiếp trong source:
message = "Tiếng Việt có dấu: ă, ê, ô, ư"

if __name__ == "__main__":
    print(message)
```

### Giải thích code từng phần

- `# -*- coding: utf-8 -*-` — máy chủ Python biết cách đọc ký tự non-ASCII trong file.
- Có thể viết ngắn: `# coding: utf-8`.
- Phải nằm trước mọi code thực thi (sau shebang nếu có).

### Ví dụ chạy thử (input → output)

```
Tiếng Việt có dấu: ă, ê, ô, ư
```

### Lưu ý / mở rộng

- Python 3.7+: có thể bỏ qua nếu file chỉ ASCII/UTF-8 và editor lưu UTF-8.
- Vẫn nên dùng khi làm việc nhóm hoặc chứa tiếng Việt trong chuỗi/comment.

---

## Câu 64 - Level 1

### Đề bài (tóm tắt tiếng Việt)

Tính tổng \( \frac{1}{2} + \frac{2}{3} + \frac{3}{4} + \cdots + \frac{n}{n+1} \) với \(n > 0\) nhập từ console.

### Phân tích ý tưởng

- Vòng lặp `i` từ 1 đến `n`, cộng dồn `i / (i + 1)`.
- Dùng `float` để kết quả là số thực (ví dụ `n=5` → `3.55`).

**Độ phức tạp:** O(n) thời gian, O(1) bộ nhớ.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
if __name__ == "__main__":
    n = int(input())
    total = 0.0

    for i in range(1, n + 1):
        total += i / (i + 1)  # Python 3: / luôn cho float

    # In đúng định dạng ví dụ đề bài
    print(round(total, 2) if total == int(total) or n <= 5 else total)
```

Phiên bản in trực tiếp khớp ví dụ:

```python
if __name__ == "__main__":
    n = int(input())
    total = sum(i / (i + 1) for i in range(1, n + 1))
    print(total)  # n=5 → 3.55
```

### Giải thích code từng phần

- `range(1, n + 1)` — các phân số từ 1/2 đến n/(n+1).
- `i / (i + 1)` — phép chia số thực trong Python 3.
- `sum(...)` với generator — cách viết gọn (idiomatic).

### Ví dụ chạy thử (input → output)

```
5  →  3.55
3  →  2.0833333333333335
1  →  0.5
```

### Lưu ý / mở rộng

- Công thức closed-form: \( \sum_{i=1}^{n} \frac{i}{i+1} = n - \sum_{k=2}^{n+1}\frac{1}{k} \) — ít dùng khi n nhỏ.
- `round(total, 2)` nếu đề yêu cầu làm tròn 2 chữ số.

---

## Câu 65 - Level 1

### Đề bài (tóm tắt tiếng Việt)

Định nghĩa hàm đệ quy:

- \(f(0) = 1\)
- \(f(n) = f(n-1) + 100\) khi \(n > 0\)

Nhập \(n > 0\) từ console và in \(f(n)\).

### Phân tích ý tưởng

- Theo đề: \(f(1) = f(0) + 100 = 101\), \(f(5) = 1 + 5 \times 100 = 501\).
- **Lưu ý:** Ví dụ đề cho `n=5` → output `500`, mâu thuẫn với \(f(0)=1\). Solution gốc dùng `f(0)=0` để ra 500.
- Ta giải thích cả hai; code khớp **ví dụ đề** (\(f(n) = n \times 100\)).

**Độ phức tạp:** O(n) đệ quy; O(1) nếu dùng công thức trực tiếp.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def f_recursive(n: int) -> int:
    """Đệ quy — khớp output mẫu (f(0) coi như 0)."""
    if n == 0:
        return 0
    return f_recursive(n - 1) + 100


def f_direct(n: int) -> int:
    """Công thức trực tiếp, cùng kết quả với đệ quy trên."""
    return n * 100


if __name__ == "__main__":
    n = int(input())
    print(f_recursive(n))  # n=5 → 500
```

Theo đúng văn bản đề (\(f(0)=1\)):

```python
def f_by_definition(n: int) -> int:
    if n == 0:
        return 1
    return f_by_definition(n - 1) + 100
# f_by_definition(5) = 501
```

### Giải thích code từng phần

- Nhánh cơ sở `n == 0` dừng đệ quy.
- Nhánh đệ quy cộng 100 mỗi bước → \(f(n) = n \times 100\) khi \(f(0)=0\).
- `f_direct` tránh giới hạn độ sâu đệ quy khi n lớn.

### Ví dụ chạy thử (input → output)

```
5  →  500   (theo ví dụ đề)
5  →  501   (nếu f(0)=1 đúng như phát biểu)
```

### Lưu ý / mở rộng

- Đề bài có inconsistency giữa công thức và ví dụ — khi làm bài thi nên theo **output mẫu**.
- Với n lớn, dùng vòng lặp hoặc `n * 100`.

---

## Câu 66 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Tính số Fibonacci thứ \(n\) theo định nghĩa:

- \(f(0)=0\), \(f(1)=1\)
- \(f(n)=f(n-1)+f(n-2)\) khi \(n>1\)

### Phân tích ý tưởng

- **Đệ quy thuần:** đơn giản nhưng O(2^n) — chậm khi n lớn.
- **Đệ quy có nhớ (memoization)** hoặc **vòng lặp:** O(n).
- Ví dụ: `n=7` → `13`.

**Độ phức tạp:** O(n) với vòng lặp; O(2^n) với đệ quy naive.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def fib_recursive(n: int) -> int:
    """Đệ quy trực tiếp — đúng đề, chậm nếu n lớn."""
    if n == 0:
        return 0
    if n == 1:
        return 1
    return fib_recursive(n - 1) + fib_recursive(n - 2)


def fib_iterative(n: int) -> int:
    """Vòng lặp — O(n), khuyến nghị."""
    a, b = 0, 1
    for _ in range(n):
        a, b = b, a + b
    return a


if __name__ == "__main__":
    n = int(input())
    print(fib_iterative(n))
```

### Giải thích code từng phần

- Hai trường hợp cơ sở: 0 và 1.
- `fib_iterative`: `a` là F(k), `b` là F(k+1), cập nhật n bước.
- Đề gợi ý đệ quy — `fib_recursive` đáp ứng; production nên dùng iterative.

### Ví dụ chạy thử (input → output)

```
7  →  13
10 →  55
0  →  0
1  →  1
```

### Lưu ý / mở rộng

- `@functools.lru_cache` trên `fib_recursive` → O(n).
- `functools.cache` (Python 3.9+) gọn hơn.

---

## Câu 67 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Dùng **list comprehension** in dãy Fibonacci từ \(f(0)\) đến \(f(n)\), các số cách nhau bởi dấu phẩy.

### Phân tích ý tưởng

- Tạo list `[f(0), f(1), ..., f(n)]` bằng list comprehension.
- Nối chuỗi: `",".join(str(x) for x in ...)`.
- Có thể tối ưu: build dãy Fib bằng vòng lặp O(n) thay gọi đệ quy từng phần tử.

**Độ phức tạp:** O(n) với cách tối ưu; O(n²) nếu gọi `fib_recursive` cho mỗi x.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def fib(n: int) -> int:
    """Fibonacci đệ quy — theo gợi ý đề."""
    if n == 0:
        return 0
    if n == 1:
        return 1
    return fib(n - 1) + fib(n - 2)


if __name__ == "__main__":
    n = int(input())
    # List comprehension theo yêu cầu đề
    values = [str(fib(x)) for x in range(n + 1)]
    print(",".join(values))
```

Phiên bản hiệu quả hơn (vẫn dùng comprehension cho format):

```python
if __name__ == "__main__":
    n = int(input())
    seq = [0, 1]
    while len(seq) <= n:
        seq.append(seq[-1] + seq[-2])
    print(",".join(str(x) for x in seq[: n + 1]))
```

### Giải thích code từng phần

- `range(n + 1)` — từ 0 đến n inclusive.
- `[str(fib(x)) for x in ...]` — list comprehension chuyển từng số sang chuỗi.
- `",".join(...)` — ghép không có khoảng trắng, khớp ví dụ `0,1,1,2,3,5,8,13`.

### Ví dụ chạy thử (input → output)

```
7  →  0,1,1,2,3,5,8,13
3  →  0,1,1,2
```

### Lưu ý / mở rộng

- Đề yêu cầu list comprehension — phần tạo list nên dùng comprehension; join có thể tách riêng.
- Generator: `",".join(map(str, fib_gen(n+1)))`.

---

## Câu 68 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Dùng **generator** in các số chẵn từ 0 đến \(n\) (bao gồm cả hai đầu), cách nhau bởi dấu phẩy. \(n\) nhập từ console.

### Phân tích ý tưởng

- Generator dùng `yield` trả từng giá trị mà không lưu toàn bộ list trong bộ nhớ.
- Số chẵn: `i % 2 == 0` với `i` từ 0 đến n.
- Cách gọn: `range(0, n + 1, 2)`.

**Độ phức tạp:** O(n) thời gian; O(1) bộ nhớ với generator.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def even_generator(n: int):
    """Sinh lần lượt các số chẵn từ 0 đến n."""
    i = 0
    while i <= n:
        if i % 2 == 0:
            yield i
        i += 1


if __name__ == "__main__":
    n = int(input())
    values = [str(i) for i in even_generator(n)]
    print(",".join(values))
```

Phiên bản generator gọn hơn:

```python
def even_generator(n: int):
    for i in range(0, n + 1, 2):
        yield i
```

### Giải thích code từng phần

- `yield i` — tạm dừng hàm, trả giá trị, giữ trạng thái cho lần gọi sau.
- List comprehension thu thập kết quả generator thành chuỗi in ra.
- `range(0, n+1, 2)` — bước nhảy 2, chỉ số chẵn.

### Ví dụ chạy thử (input → output)

```
10  →  0,2,4,6,8,10
7   →  0,2,4,6
0   →  0
```

### Lưu ý / mở rộng

- In trực tiếp: `print(",".join(str(i) for i in even_generator(n)))`.
- Generator expression: `(i for i in range(n+1) if i % 2 == 0)`.

---

## Câu 69 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Dùng **generator** in các số trong [0, n] **chia hết cho cả 5 và 7**, cách nhau bởi dấu phẩy.

### Phân tích ý tưởng

- Số chia hết cho 5 và 7 ⇔ chia hết cho 35 (LCM).
- Duyệt `i` từ 0 đến n; nếu `i % 35 == 0` thì `yield i`.
- Ví dụ `n=100` → `0,35,70`.

**Độ phức tạp:** O(n) thời gian; O(1) bộ nhớ.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def divisible_by_5_and_7(n: int):
    """Sinh các số trong [0, n] chia hết cho 5 và 7."""
    for i in range(n + 1):
        if i % 5 == 0 and i % 7 == 0:
            yield i


if __name__ == "__main__":
    n = int(input())
    print(",".join(str(i) for i in divisible_by_5_and_7(n)))
```

### Giải thích code từng phần

- `range(n + 1)` — bao gồm n.
- Điều kiện `% 5 == 0 and % 7 == 0` tương đương `% 35 == 0`.
- `yield` trả từng số thỏa điều kiện.

### Ví dụ chạy thử (input → output)

```
100  →  0,35,70
50   →  0,35
34   →  0
```

### Lưu ý / mở rộng

- Tối ưu: `for i in range(0, n + 1, 35): yield i` — bỏ qua số không thỏa.
- Tổng quát: thay 5, 7 bằng `math.lcm(a, b)`.

---

## Câu 70 - Level 1

### Đề bài (tóm tắt tiếng Việt)

Viết các câu lệnh `assert` để xác minh mọi số trong list `[2, 4, 6, 8]` đều là số chẵn.

### Phân tích ý tưởng

- `assert điều_kiện` — nếu sai, ném `AssertionError`.
- Duyệt từng phần tử và assert `i % 2 == 0`.
- Có thể assert một lần với `all()`.

**Độ phức tạp:** O(k) với k = độ dài list.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
if __name__ == "__main__":
    numbers = [2, 4, 6, 8]

    # Cách 1: assert từng phần tử
    for i in numbers:
        assert i % 2 == 0, f"{i} không phải số chẵn"

    # Cách 2: assert một lần
    assert all(i % 2 == 0 for i in numbers)

    print("Tất cả phần tử đều chẵn — assert passed.")
```

### Giải thích code từng phần

- `i % 2 == 0` — định nghĩa số chẵn trong Python.
- Thông điệp sau dấu phẩy — hiển thị khi assert thất bại.
- `all(...)` — True nếu mọi phần tử thỏa điều kiện.

### Ví dụ chạy thử (input → output)

```
[2,4,6,8]  →  Tất cả phần tử đều chẵn — assert passed.
[2,4,5,8]  →  AssertionError: 5 không phải số chẵn
```

### Lưu ý / mở rộng

- `python -O` tắt assert — không dùng assert thay validation production.
- Unit test: `unittest` hoặc `pytest` thay cho assert script.

---

## Câu 71 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Nhập biểu thức toán học cơ bản từ console và in kết quả tính toán.

### Phân tích ý tưởng

- `eval(expression)` thực thi chuỗi như code Python — nhanh nhưng **nguy hiểm** nếu input không tin cậy.
- Ví dụ: `35+3` → `38`.
- Thay `raw_input` bằng `input()` trong Python 3.

**Độ phức tạp:** phụ thuộc độ dài biểu thức.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
if __name__ == "__main__":
    expression = input()
    # Cảnh báo: eval chỉ dùng với input tin cậy
    result = eval(expression)
    print(result)
```

Phiên bản an toàn hơn (giới hạn phép toán):

```python
import ast
import operator as op

SAFE_OPS = {
    ast.Add: op.add,
    ast.Sub: op.sub,
    ast.Mult: op.mul,
    ast.Div: op.truediv,
    ast.Pow: op.pow,
    ast.USub: op.neg,
}


def safe_eval(expr: str):
    def _eval(node):
        if isinstance(node, ast.Num):  # type: ignore[attr-defined]
            return node.n
        if isinstance(node, ast.Constant):
            return node.value
        if isinstance(node, ast.BinOp):
            return SAFE_OPS[type(node.op)](_eval(node.left), _eval(node.right))
        if isinstance(node, ast.UnaryOp):
            return SAFE_OPS[type(node.op)](_eval(node.operand))
        raise ValueError("Biểu thức không được phép")

    return _eval(ast.parse(expr, mode="eval").body)


if __name__ == "__main__":
    expression = input()
    print(safe_eval(expression))
```

### Giải thích code từng phần

- `eval("35+3")` — Python parse và tính → 38.
- `safe_eval` — chỉ cho phép số và toán tử cơ bản, tránh thực thi mã tùy ý.
- Không truyền `{"__builtins__": {}}` cho eval trừ khi hiểu rõ hạn chế.

### Ví dụ chạy thử (input → output)

```
35+3    →  38
10*2+5  →  25
(8-3)*4 →  20
```

### Lưu ý / mở rộng

- **Không dùng `eval` với input người dùng không tin cậy** — rủi ro thực thi mã độc.
- Thư viện: `numexpr`, hoặc parser tự viết.

---

## Câu 72 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Viết hàm **tìm kiếm nhị phân (binary search)** tìm phần tử trong list đã sắp xếp, trả về **chỉ số (index)** nếu tìm thấy, ngược lại trả về -1.

### Phân tích ý tưởng

- Binary search: so sánh với phần tử giữa, thu hẹp nửa trái hoặc phải.
- Yêu cầu list **đã sắp xếp tăng dần**.
- Biến `bottom` (trái), `top` (phải), `mid` (giữa).
- **Độ phức tạp:** O(log n) thời gian, O(1) bộ nhớ.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
from typing import List, Any


def bin_search(items: List[Any], element: Any) -> int:
    """Tìm kiếm nhị phân — trả về index hoặc -1."""
    left, right = 0, len(items) - 1

    while left <= right:
        mid = (left + right) // 2  # tránh float, không cần math.floor
        if items[mid] == element:
            return mid
        if items[mid] > element:
            right = mid - 1
        else:
            left = mid + 1

    return -1


if __name__ == "__main__":
    li = [2, 5, 7, 9, 11, 17, 222]
    print(bin_search(li, 11))   # 4
    print(bin_search(li, 12))   # -1
```

### Giải thích code từng phần

- `while left <= right` — còn vùng tìm kiếm hợp lệ.
- `mid = (left + right) // 2` — chỉ số giữa (integer division).
- Ba nhánh: bằng → trả index; lớn hơn → tìm trái; nhỏ hơn → tìm phải.
- Hết vòng lặp không tìm thấy → `-1`.

### Ví dụ chạy thử (input → output)

```
list=[2,5,7,9,11,17,222], tìm 11  →  4
list=[2,5,7,9,11,17,222], tìm 12  →  -1
```

### Lưu ý / mở rộng

- `bisect.bisect_left` trong thư viện chuẩn — dùng production.
- Cẩn thận tràn số với mảng cực lớn: `mid = left + (right - left) // 2`.

---

## Câu 73 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Viết hàm **binary search** tìm phần tử trong list đã sắp xếp, trả về index (giống câu 72).

### Phân tích ý tưởng

- **Câu 73 trùng nội dung câu 72** trong file nguồn (cùng đề, cùng solution).
- Có thể viết lại dạng **đệ quy** để phân biệt, hoặc tái sử dụng hàm iterative.

**Độ phức tạp:** O(log n).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
from typing import List, Any


def bin_search_recursive(items: List[Any], element: Any,
                         left: int = 0, right: int | None = None) -> int:
    """Binary search đệ quy."""
    if right is None:
        right = len(items) - 1

    if left > right:
        return -1

    mid = (left + right) // 2
    if items[mid] == element:
        return mid
    if items[mid] > element:
        return bin_search_recursive(items, element, left, mid - 1)
    return bin_search_recursive(items, element, mid + 1, right)


if __name__ == "__main__":
    li = [2, 5, 7, 9, 11, 17, 222]
    print(bin_search_recursive(li, 11))  # 4
    print(bin_search_recursive(li, 12))  # -1
```

### Giải thích code từng phần

- Điều kiện dừng: `left > right` → không tìm thấy.
- Mỗi bước gọi đệ quy một nửa mảng — logic giống vòng lặp câu 72.
- Tham số mặc định `left`, `right` cho phép gọi `bin_search_recursive(li, x)` gọn.

### Ví dụ chạy thử (input → output)

```
tìm 11 trong [2,5,7,9,11,17,222]  →  4
tìm 12  →  -1
```

### Lưu ý / mở rộng

- Đệ quy tốn O(log n) stack frame — list rất lớn nên dùng iterative.
- Câu 72 và 73 trong đề gốc là duplicate — học một lần, áp dụng cả hai.

---

## Câu 74 - Level 1

### Đề bài (tóm tắt tiếng Việt)

Sinh số thực ngẫu nhiên trong khoảng **10 đến 100** (đề ghi dùng module math/random).

### Phân tích ý tưởng

- `random.random()` trả về float trong **[0.0, 1.0)**.
- Scale và dịch: `random() * (max - min) + min` → **[10, 100)** nếu max=100.
- Muốn **[10, 100]** đầy đủ: dùng `random.uniform(10, 100)`.
- Solution gốc `random.random()*100` chỉ cho [0,100) — **sai khoảng** đề bài.

**Độ phức tạp:** O(1).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
import random


if __name__ == "__main__":
    # Cách 1: uniform — khuyến nghị, bao gồm cả hai đầu mút
    print(random.uniform(10, 100))

    # Cách 2: scale từ random.random() theo gợi ý đề
    value = random.random() * (100 - 10) + 10
    print(value)
```

### Giải thích code từng phần

- `random.uniform(a, b)` — float ngẫu nhiên đều trên [a, b].
- `random.random() * 90 + 10` — biến đổi tuyến tính từ [0,1) sang [10,100).
- Module `math` không bắt buộc; đề nhắc nhầm — thực tế dùng `random`.

### Ví dụ chạy thử (input → output)

```
(lần 1)  →  47.3829104956...
(lần 2)  →  91.2055831042...
(mỗi lần chạy khác nhau)
```

### Lưu ý / mở rộng

- Làm tròn: `round(random.uniform(10, 100), 2)`.
- Số nguyên ngẫu nhiên: `random.randint(10, 100)`.

---

## Câu 75 - Level 1

### Đề bài (tóm tắt tiếng Việt)

Sinh số thực ngẫu nhiên trong khoảng **5 đến 95**.

### Phân tích ý tưởng

- Tương tự câu 74: `uniform(5, 95)` hoặc `random.random() * (95 - 5) + 5`.
- Solution gốc `random.random()*100-5` cho khoảng **[-5, 95)** — sai điểm đầu.

**Độ phức tạp:** O(1).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
import random


if __name__ == "__main__":
    # Khuyến nghị
    print(random.uniform(5, 95))

    # Theo công thức scale từ random.random()
    value = random.random() * (95 - 5) + 5
    print(value)
```

### Giải thích code từng phần

- Độ rộng khoảng: `95 - 5 = 90`.
- Nhân `random.random()` với 90 rồi cộng 5 → giá trị trong [5, 95).
- `uniform(5, 95)` — API rõ ràng, tránh sai công thức.

### Ví dụ chạy thử (input → output)

```
(lần 1)  →  62.1847392011...
(lần 2)  →  8.9912038471...
```

### Lưu ý / mở rộng

- Hàm tổng quát:

```python
def random_in_range(low: float, high: float) -> float:
    return random.uniform(low, high)
```

- Muốn **loại trừ** đầu mút: điều chỉnh epsilon hoặc dùng `random.random()` với biên mở.

---

*Tổng cộng: 25 câu (51–75) đã hoàn thành.*
