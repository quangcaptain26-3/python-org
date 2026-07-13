# Lời giải chi tiết Python - Câu 76 đến 100

Tài liệu này cung cấp lời giải chi tiết bằng tiếng Việt cho các bài tập Python 3 từ Question 76 đến Question 100.

---

## Câu 76 - Level 1

### Đề bài (tóm tắt tiếng Việt)

Viết chương trình in ra một **số chẵn ngẫu nhiên** trong khoảng từ 0 đến 10 (bao gồm cả hai đầu), sử dụng module `random` và **list comprehension**.

### Phân tích ý tưởng

1. Liệt kê tất cả số chẵn từ 0 đến 10 bằng list comprehension: `[i for i in range(11) if i % 2 == 0]`.
2. Dùng `random.choice()` để chọn ngẫu nhiên một phần tử từ danh sách đó.
3. In kết quả.

**Độ phức tạp:** O(1) vì danh sách chỉ có 6 phần tử cố định.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
import random

# Tạo danh sách các số chẵn từ 0 đến 10
even_numbers = [i for i in range(11) if i % 2 == 0]

# Chọn ngẫu nhiên một số chẵn và in ra
print(random.choice(even_numbers))
```

### Giải thích code từng phần

- `range(11)` tạo dãy 0, 1, 2, ..., 10.
- Điều kiện `i % 2 == 0` giữ lại các số chia hết cho 2 → `[0, 2, 4, 6, 8, 10]`.
- `random.choice(even_numbers)` trả về một phần tử được chọn ngẫu nhiên từ danh sách.

### Ví dụ chạy thử (input → output)

Không cần input. Mỗi lần chạy có thể ra kết quả khác nhau:

```
6
```

```
0
```

```
10
```

### Lưu ý / mở rộng

Có thể viết gọn trong một dòng như đề gốc, hoặc dùng `random.randrange(0, 11, 2)` để chọn trực tiếp số chẵn mà không cần tạo list.

---

## Câu 77 - Level 1

### Đề bài (tóm tắt tiếng Việt)

Viết chương trình in ra một **số ngẫu nhiên chia hết cho cả 5 và 7** trong khoảng từ 0 đến 10 (bao gồm cả hai đầu), dùng `random` và list comprehension.

### Phân tích ý tưởng

1. Một số chia hết cho cả 5 và 7 phải chia hết cho **BCNN(5, 7) = 35**.
2. Trong khoảng [0, 10], chỉ có **duy nhất số 0** thỏa mãn.
3. Dùng list comprehension lọc các số thỏa điều kiện, rồi `random.choice()` chọn ngẫu nhiên.

**Lưu ý:** Code gốc trong đề dùng `range(201)` — đó là lỗi, không khớp yêu cầu 0–10.

**Độ phức tạp:** O(n) với n = 11 (rất nhỏ).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
import random

# Lọc các số trong [0, 10] chia hết cho cả 5 và 7
candidates = [i for i in range(11) if i % 5 == 0 and i % 7 == 0]

print(random.choice(candidates))  # Luôn in ra 0
```

### Giải thích code từng phần

- `i % 5 == 0 and i % 7 == 0` đảm bảo số chia hết cho cả hai.
- `candidates` chỉ chứa `[0]`.
- `random.choice` với một phần tử duy nhất luôn trả về 0.

### Ví dụ chạy thử (input → output)

```
0
```

(Mọi lần chạy đều ra 0 vì chỉ có một lựa chọn hợp lệ.)

### Lưu ý / mở rộng

Nếu mở rộng khoảng lên 0–200, danh sách sẽ là `[0, 35, 70, 105, 140, 175]`. Có thể dùng `i % 35 == 0` thay vì kiểm tra cả hai điều kiện.

---

## Câu 78 - Level 1

### Đề bài (tóm tắt tiếng Việt)

Viết chương trình tạo một **danh sách gồm 5 số ngẫu nhiên** trong khoảng từ 100 đến 200 (bao gồm cả hai đầu).

### Phân tích ý tưởng

1. Dùng `random.sample()` để lấy **5 số không trùng nhau** từ một tập hợp.
2. Tập hợp nguồn: `range(100, 201)` tương ứng các số từ 100 đến 200.

**Lưu ý:** Code gốc dùng `range(100)` (0–99) — sai so với đề bài.

**Độ phức tạp:** O(k) với k = 5, thuật toán sample của Python hiệu quả.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
import random

# Lấy 5 số ngẫu nhiên không trùng từ [100, 200]
result = random.sample(range(100, 201), 5)
print(result)
```

### Giải thích code từng phần

- `range(100, 201)` tạo dãy 100, 101, ..., 200 (201 không bao gồm).
- `random.sample(population, k)` trả về list k phần tử **không lặp**, thứ tự ngẫu nhiên.

### Ví dụ chạy thử (input → output)

```
[142, 178, 103, 156, 199]
```

```
[100, 115, 187, 134, 200]
```

### Lưu ý / mở rộng

- Nếu **cho phép trùng**, dùng `[random.randint(100, 200) for _ in range(5)]`.
- `random.sample` yêu cầu `k <= len(population)`; ở đây 5 ≤ 101 nên hợp lệ.

---

## Câu 79 - Level 1

### Đề bài (tóm tắt tiếng Việt)

Viết chương trình tạo ngẫu nhiên một **danh sách 5 số chẵn** trong khoảng từ 100 đến 200 (bao gồm cả hai đầu).

### Phân tích ý tưởng

1. Tạo danh sách tất cả số chẵn từ 100 đến 200 bằng list comprehension.
2. Dùng `random.sample()` lấy 5 số không trùng từ danh sách đó.

Có `(200 - 100) // 2 + 1 = 51` số chẵn → đủ để lấy 5 số.

**Độ phức tạp:** O(n) với n = 51 để tạo list, O(5) để sample.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
import random

# Danh sách số chẵn từ 100 đến 200
evens = [i for i in range(100, 201) if i % 2 == 0]

# Chọn ngẫu nhiên 5 số chẵn không trùng
print(random.sample(evens, 5))
```

### Giải thích code từng phần

- List comprehension lọc số chẵn trong khoảng cho trước.
- `random.sample(evens, 5)` đảm bảo 5 số khác nhau và đều là số chẵn.

### Ví dụ chạy thử (input → output)

```
[120, 186, 104, 158, 200]
```

### Lưu ý / mở rộng

Có thể tạo số chẵn trực tiếp: `range(100, 201, 2)` thay vì lọc bằng `% 2`.

---

## Câu 80 - Level 1

### Đề bài (tóm tắt tiếng Việt)

Viết chương trình tạo ngẫu nhiên một **danh sách 5 số chia hết cho cả 5 và 7** trong khoảng từ 1 đến 1000 (bao gồm cả hai đầu).

### Phân tích ý tưởng

1. Số chia hết cho 5 và 7 ↔ chia hết cho 35.
2. Tạo danh sách ứng viên: `[35, 70, 105, ..., 980]` (khoảng 28 số).
3. Dùng `random.sample()` lấy 5 số.

**Độ phức tạp:** O(n) với n ≈ 28.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
import random

# Các số chia hết cho 35 trong [1, 1000]
candidates = [i for i in range(1, 1001) if i % 35 == 0]

print(random.sample(candidates, 5))
```

### Giải thích code từng phần

- `i % 35 == 0` tương đương `i % 5 == 0 and i % 7 == 0`.
- `range(1, 1001)` bao gồm 1 đến 1000.
- `random.sample` chọn 5 phần tử không trùng.

### Ví dụ chạy thử (input → output)

```
[315, 70, 980, 175, 420]
```

### Lưu ý / mở rộng

Có thể tạo trực tiếp: `list(range(35, 1001, 35))` — gọn và nhanh hơn list comprehension.

---

## Câu 81 - Level 1

### Đề bài (tóm tắt tiếng Việt)

Viết chương trình in ngẫu nhiên một **số nguyên** trong khoảng từ 7 đến 15 (bao gồm cả hai đầu).

### Phân tích ý tưởng

Dùng `random.randrange(start, stop)` — tham số `stop` **không bao gồm**, nên dùng `randrange(7, 16)` để lấy 7..15.

**Độ phức tạp:** O(1).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
import random

# randrange(7, 16) → số nguyên từ 7 đến 15
print(random.randrange(7, 16))
```

### Giải thích code từng phần

- `random.randrange(a, b)` trả về số nguyên ngẫu nhiên trong `[a, b)` — nửa mở bên phải.
- `16` là giới hạn trên (không lấy), nên kết quả tối đa là 15.

### Ví dụ chạy thử (input → output)

```
11
```

```
7
```

```
15
```

### Lưu ý / mở rộng

`random.randint(7, 15)` cũng phù hợp — cả hai đầu **đều bao gồm**, dễ nhớ hơn cho người mới.

---

## Câu 82 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Viết chương trình **nén (compress)** và **giải nén (decompress)** chuỗi `"hello world!hello world!hello world!hello world!"` bằng module `zlib`.

### Phân tích ý tưởng

1. `zlib` chỉ làm việc với **dữ liệu dạng bytes**, không phải `str`.
2. Chuyển chuỗi sang bytes (UTF-8), nén bằng `zlib.compress()`.
3. Giải nén bằng `zlib.decompress()`, decode về chuỗi.

**Độ phức tạp:** O(n) với n là độ dài chuỗi.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
import zlib

text = "hello world!hello world!hello world!hello world!"

# Chuyển str → bytes trước khi nén
data = text.encode("utf-8")
compressed = zlib.compress(data)

print("Dữ liệu nén (bytes):", compressed)
print("Giải nén:", zlib.decompress(compressed).decode("utf-8"))
```

### Giải thích code từng phần

- `.encode("utf-8")` chuyển chuỗi Unicode thành bytes.
- `zlib.compress()` trả về bytes đã nén (thường ngắn hơn nếu có nhiều lặp lại).
- `zlib.decompress()` khôi phục bytes gốc.
- `.decode("utf-8")` chuyển bytes về chuỗi đọc được.

### Ví dụ chạy thử (input → output)

```
Dữ liệu nén (bytes): b'x\x9c\xcbH\xcd\xc9\xc9W(\xcf/\xcaI\xe1\x02\x00}\xdf\x0e\x07'
Giải nén: hello world!hello world!hello world!hello world!
```

(Giá trị bytes nén có thể khác tùy phiên bản zlib, nhưng giải nén luôn đúng.)

### Lưu ý / mở rộng

- Với chuỗi lặp nhiều, nén zlib hiệu quả rõ rệt.
- Có thể dùng `gzip` cho file lớn hoặc khi cần định dạng file `.gz`.

---

## Câu 83 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Viết chương trình in **thời gian chạy** của việc thực thi biểu thức `1+1` lặp 100 lần.

### Phân tích ý tưởng

Dùng module `timeit` — chuyên đo thời gian thực thi code Python.

- `Timer(stmt)` tạo bộ đo với câu lệnh cần đo.
- `.timeit()` chạy nhiều lần và trả về tổng thời gian (giây).

**Độ phức tạp:** Đo thực tế, không phải độ phức tạp thuật toán.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
from timeit import Timer

# Đo thời gian chạy vòng lặp 100 lần phép 1+1
timer = Timer("for _ in range(100): 1 + 1")
print(f"Thời gian (giây): {timer.timeit()}")
```

### Giải thích code từng phần

- `Timer` nhận chuỗi Python sẽ được `exec`.
- `timeit()` mặc định chạy 1.000.000 lần (có thể chỉnh bằng tham số `number`).
- Kết quả rất nhỏ (micro giây) vì `1+1` cực nhanh.

### Ví dụ chạy thử (input → output)

```
Thời gian (giây): 0.012345678901234567
```

(Giá trị cụ thể phụ thuộc máy; thường < 0.1 giây.)

### Lưu ý / mở rộng

- Dùng `timeit.timeit("1+1", number=100)` gọn hơn cho trường hợp đơn giản.
- Với code phức tạp, nên dùng `time.perf_counter()` hoặc profiling (`cProfile`).

---

## Câu 84 - Level 1

### Đề bài (tóm tắt tiếng Việt)

Viết chương trình **xáo trộn (shuffle)** và in danh sách `[3, 6, 7, 8]`.

### Phân tích ý tưởng

Dùng `random.shuffle()` — xáo trộn list **tại chỗ** (in-place), không trả về list mới.

**Độ phức tạp:** O(n) với n = 4.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
from random import shuffle

li = [3, 6, 7, 8]
shuffle(li)  # Sửa trực tiếp list li
print(li)
```

### Giải thích code từng phần

- `shuffle(li)` hoán đổi vị trí các phần tử ngẫu nhiên trong chính list `li`.
- Hàm trả về `None`; kết quả nằm trong `li`.

### Ví dụ chạy thử (input → output)

```
[7, 3, 8, 6]
```

```
[8, 6, 3, 7]
```

### Lưu ý / mở rộng

Nếu cần giữ list gốc: `shuffled = li.copy(); shuffle(shuffled)`.

---

## Câu 85 - Level 1

### Đề bài (tóm tắt tiếng Việt)

Viết chương trình **xáo trộn** và in danh sách `[3, 6, 7, 8]`.

*(Trùng nội dung với Câu 84 — có thể là bài lặp trong đề gốc.)*

### Phân tích ý tưởng

Giống Câu 84: dùng `random.shuffle()` để xáo trộn list tại chỗ.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
from random import shuffle

numbers = [3, 6, 7, 8]
shuffle(numbers)
print(numbers)
```

### Giải thích code từng phần

- `shuffle` dùng thuật toán Fisher-Yates, đảm bảo mọi hoán vị có xác suất bằng nhau (với RNG tốt).

### Ví dụ chạy thử (input → output)

```
[6, 8, 3, 7]
```

### Lưu ý / mở rộng

`random.sample(numbers, len(numbers))` tạo bản sao đã xáo mà không sửa list gốc.

---

## Câu 86 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Viết chương trình sinh **tất cả các câu** từ tổ hợp:
- Chủ ngữ: `["I", "You"]`
- Động từ: `["Play", "Love"]`
- Tân ngữ: `["Hockey", "Football"]`

Ví dụ: `"I Play Hockey."`

### Phân tích ý tưởng

Bài toán **tích Descartes** của 3 tập — dùng 3 vòng lặp lồng nhau (hoặc `itertools.product`).

Tổng số câu: 2 × 2 × 2 = **8 câu**.

**Độ phức tạp:** O(n × m × p).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
subjects = ["I", "You"]
verbs = ["Play", "Love"]
objects = ["Hockey", "Football"]

for subject in subjects:
    for verb in verbs:
        for obj in objects:
            print(f"{subject} {verb} {obj}.")
```

### Giải thích code từng phần

- Ba vòng `for` lồng nhau duyệt mọi tổ hợp (subject, verb, object).
- f-string ghép câu và thêm dấu chấm cuối.

### Ví dụ chạy thử (input → output)

```
I Play Hockey.
I Play Football.
I Love Hockey.
I Love Football.
You Play Hockey.
You Play Football.
You Love Hockey.
You Love Football.
```

### Lưu ý / mở rộng

Cách Pythonic hơn:

```python
from itertools import product
for s, v, o in product(subjects, verbs, objects):
    print(f"{s} {v} {o}.")
```

---

## Câu 87 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Dùng list comprehension, in danh sách sau khi **xóa các số chẵn** khỏi `[5, 6, 77, 45, 22, 12, 24]`.

### Phân tích ý tưởng

Giữ lại phần tử `x` khi `x % 2 != 0` (số lẻ).

**Độ phức tạp:** O(n) với n = 7.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
li = [5, 6, 77, 45, 22, 12, 24]

# Giữ số lẻ, loại số chẵn
li = [x for x in li if x % 2 != 0]
print(li)
```

### Giải thích code từng phần

- List comprehension tạo list mới, không sửa list cũ trong quá trình duyệt (an toàn).
- `x % 2 != 0` → số lẻ.

### Ví dụ chạy thử (input → output)

```
[5, 77, 45]
```

### Lưu ý / mở rộng

Không nên xóa phần tử khi đang `for` trực tiếp trên cùng list — dễ bỏ sót phần tử.

---

## Câu 88 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Dùng list comprehension, in danh sách sau khi **xóa các số chia hết cho cả 5 và 7** khỏi `[12, 24, 35, 70, 88, 120, 155]`.

### Phân tích ý tưởng

Giữ phần tử **không** chia hết cho cả 5 và 7:
- Điều kiện loại: `x % 5 == 0 and x % 7 == 0`
- Điều kiện giữ: phủ định của trên

**Độ phức tạp:** O(n).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
li = [12, 24, 35, 70, 88, 120, 155]

# Loại số chia hết cho 35 (tức cả 5 và 7)
li = [x for x in li if not (x % 5 == 0 and x % 7 == 0)]
print(li)
```

### Giải thích code từng phần

- 35, 70 chia hết cho 35 → bị loại.
- 120 chia hết cho 5 nhưng không chia hết cho 7 → **giữ lại**.
- 155 chia hết cho 5, không chia hết cho 7 → giữ.

### Ví dụ chạy thử (input → output)

```
[12, 24, 88, 120, 155]
```

### Lưu ý / mở rộng

Tương đương: `x % 35 != 0` khi muốn loại số chia hết cho cả hai.

---

## Câu 89 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Dùng list comprehension, in danh sách sau khi **xóa phần tử ở vị trí 0, 2, 4, 6** (đếm từ 0) trong `[12, 24, 35, 70, 88, 120, 155]`.

### Phân tích ý tưởng

Dùng `enumerate()` để lấy cặp `(chỉ số, giá trị)`, giữ phần tử có **chỉ số lẻ** (1, 3, 5) — tức bỏ chỉ số 0, 2, 4, 6.

**Độ phức tạp:** O(n).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
li = [12, 24, 35, 70, 88, 120, 155]

# Giữ phần tử ở vị trí lẻ (1, 3, 5, ...)
li = [x for i, x in enumerate(li) if i % 2 != 0]
print(li)
```

### Giải thích code từng phần

- `enumerate(li)` → (0,12), (1,24), (2,35), (3,70), (4,88), (5,120), (6,155).
- `i % 2 != 0` giữ chỉ số 1, 3, 5 → giá trị 24, 70, 120.

### Ví dụ chạy thử (input → output)

```
[24, 70, 120]
```

### Lưu ý / mở rộng

Với tập chỉ số tùy ý: `if i not in {0, 2, 4, 6}` (như Câu 91).

---

## Câu 90 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Dùng list comprehension, tạo mảng 3 chiều kích thước **3 × 5 × 8**, mọi phần tử bằng **0**.

### Phân tích ý tưởng

List comprehension lồng nhau 3 tầng:
- Tầng ngoài: 3 "lớp" (rows)
- Tầng giữa: mỗi lớp 5 hàng
- Tầng trong: mỗi hàng 8 cột, giá trị 0

**Độ phức tạp:** O(3 × 5 × 8) = O(120) — tạo 120 phần tử.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
# Mảng 3D: 3 lớp × 5 hàng × 8 cột, toàn bộ = 0
array_3d = [
    [[0 for _ in range(8)] for _ in range(5)]
    for _ in range(3)
]
print(array_3d)
```

### Giải thích code từng phần

- `[0 for _ in range(8)]` → một hàng 8 số 0.
- Lặp 5 lần → một "mặt phẳng" 5×8.
- Lặp 3 lần → 3 mặt phẳng → tensor 3×5×8.

**Quan trọng:** Thứ tự vòng lặp từ trong ra ngoài phải khớp thứ tự kích thước (8, 5, 3).

### Ví dụ chạy thử (input → output)

```
[[[0, 0, 0, 0, 0, 0, 0, 0], [0, 0, ...], ...], [...], [...]]
```

(Cấu trúc list 3 tầng, tổng 120 số 0.)

### Lưu ý / mở rộng

Với mảng số học lớn, nên dùng **NumPy**: `numpy.zeros((3, 5, 8))` — nhanh và tiết kiệm bộ nhớ hơn.

---

## Câu 91 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Dùng list comprehension, in danh sách sau khi **xóa phần tử ở vị trí 0, 4, 5** trong `[12, 24, 35, 70, 88, 120, 155]`.

### Phân tích ý tưởng

Dùng `enumerate`, giữ phần tử có chỉ số **không** thuộc `{0, 4, 5}`.

**Độ phức tạp:** O(n).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
li = [12, 24, 35, 70, 88, 120, 155]
remove_indices = {0, 4, 5}

li = [x for i, x in enumerate(li) if i not in remove_indices]
print(li)
```

### Giải thích code từng phần

- Chỉ số 0 → 12 (bỏ), 1 → 24 (giữ), 2 → 35, 3 → 70, 4 → 88 (bỏ), 5 → 120 (bỏ), 6 → 155.
- Kết quả: `[24, 35, 70, 155]`.

### Ví dụ chạy thử (input → output)

```
[24, 35, 70, 155]
```

### Lưu ý / mở rộng

Kiểm tra `i not in {0, 4, 5}` có độ phức tạp O(1) mỗi lần — hiệu quả với tập chỉ số nhỏ.

---

## Câu 92 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Dùng list comprehension, in danh sách sau khi **xóa tất cả giá trị 24** khỏi `[12, 24, 35, 24, 88, 120, 155]`.

### Phân tích ý tưởng

Giữ phần tử `x` khi `x != 24`. List comprehension an toàn hơn `list.remove(24)` trong vòng lặp (vì `remove` chỉ xóa lần đầu mỗi lần gọi).

**Độ phức tạp:** O(n).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
li = [12, 24, 35, 24, 88, 120, 155]

# Loại mọi phần tử có giá trị 24
li = [x for x in li if x != 24]
print(li)
```

### Giải thích code từng phần

- Duyệt từng `x`, chỉ thêm vào list mới nếu khác 24.
- Cả hai số 24 (vị trí 1 và 3) đều bị loại.

### Ví dụ chạy thử (input → output)

```
[12, 35, 88, 120, 155]
```

### Lưu ý / mở rộng

`filter(lambda x: x != 24, li)` cũng được, nhưng list comprehension thường dễ đọc hơn.

---

## Câu 93 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Cho hai list `[1, 3, 6, 78, 35, 55]` và `[12, 24, 35, 24, 88, 120, 155]`, viết chương trình tạo list gồm **phần tử chung (giao)** của hai list.

### Phân tích ý tưởng

1. Chuyển mỗi list thành `set`.
2. Dùng phép giao `&` (hoặc `.intersection()`).
3. Chuyển kết quả về list.

**Lưu ý:** Thứ tự phần tử trong set không đảm bảo như list gốc.

**Độ phức tạp:** O(n + m) trung bình với hash set.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
list1 = [1, 3, 6, 78, 35, 55]
list2 = [12, 24, 35, 24, 88, 120, 155]

# Giao hai tập hợp
intersection = set(list1) & set(list2)
print(list(intersection))
```

### Giải thích code từng phần

- `set(list2)` loại trùng lặp trong list2 (hai số 24 → một).
- `&` trả về phần tử có trong cả hai set → chỉ **35**.

### Ví dụ chạy thử (input → output)

```
[35]
```

### Lưu ý / mở rộng

Giữ thứ tự theo list1:

```python
common = [x for x in list1 if x in set(list2)]
```

---

## Câu 94 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Cho list `[12, 24, 35, 24, 88, 120, 155, 88, 120, 155]`, in list sau khi **xóa trùng lặp** nhưng **giữ nguyên thứ tự** xuất hiện lần đầu.

### Phân tích ý tưởng

Duyệt list, dùng `set` để nhớ phần tử đã gặp; chỉ thêm vào list mới nếu chưa thấy.

**Độ phức tạp:** O(n).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def remove_duplicates(items):
    seen = set()
    result = []
    for item in items:
        if item not in seen:
            seen.add(item)
            result.append(item)
    return result


li = [12, 24, 35, 24, 88, 120, 155, 88, 120, 155]
print(remove_duplicates(li))
```

### Giải thích code từng phần

- `seen` tra cứu O(1) trung bình.
- Chỉ `append` lần đầu gặp mỗi giá trị → thứ tự ban đầu được bảo toàn.
- Không dùng `set(li)` trực tiếp vì mất thứ tự (trước Python 3.7) hoặc không đúng ý "lần đầu xuất hiện".

### Ví dụ chạy thử (input → output)

```
[12, 24, 35, 88, 120, 155]
```

### Lưu ý / mở rộng

Python 3.7+: `list(dict.fromkeys(li))` — ngắn gọn, giữ thứ tự insertion.

---

## Câu 95 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Định nghĩa class `Person` và hai class con `Male`, `Female`. Mỗi class có method `getGender()` trả về `"Male"` hoặc `"Female"` tương ứng.

### Phân tích ý tưởng

Áp dụng **kế thừa (inheritance)**:
- `Person` là lớp cha (có thể trả về `"Unknown"`).
- `Male`, `Female` ghi đè (override) `getGender()`.

**Độ phức tạp:** O(1) mỗi lần gọi method.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
class Person:
    """Lớp cơ sở đại diện con người."""

    def get_gender(self):
        return "Unknown"


class Male(Person):
    def get_gender(self):
        return "Male"


class Female(Person):
    def get_gender(self):
        return "Female"


if __name__ == "__main__":
    a_male = Male()
    a_female = Female()
    print(a_male.get_gender())
    print(a_female.get_gender())
```

### Giải thích code từng phần

- `class Male(Person)` — `Male` kế thừa `Person`.
- `get_gender` trong lớp con **ghi đè** method cùng tên ở lớp cha (polymorphism).
- Gọi `a_male.get_gender()` → Python tìm method trên `Male` trước.

### Ví dụ chạy thử (input → output)

```
Male
Female
```

### Lưu ý / mở rộng

- Python 3 không cần kế thừa `object` (đề gốc dùng `Person(object)` — vẫn chạy được).
- Có thể dùng `@property` hoặc `Enum` cho mô hình giới tính phức tạp hơn.

---

## Câu 96 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Viết chương trình đếm và in **số lần xuất hiện của mỗi ký tự** trong chuỗi nhập từ bàn phím.

**Ví dụ:** Input `abcdefgabc` → Output mỗi dòng `ký_tự,số_lần`.

### Phân tích ý tưởng

1. Dùng dictionary: key = ký tự, value = số lần đếm.
2. Duyệt từng ký tự, cập nhật: `dic[ch] = dic.get(ch, 0) + 1`.
3. In theo thứ tự lần đầu gặp (dict Python 3.7+ giữ insertion order).

**Độ phức tạp:** O(n) với n = độ dài chuỗi.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
s = input("Nhập chuỗi: ")

counts = {}
for ch in s:
    counts[ch] = counts.get(ch, 0) + 1

# In theo thứ tự xuất hiện lần đầu
for ch, count in counts.items():
    print(f"{ch},{count}")
```

### Giải thích code từng phần

- `input()` thay `raw_input()` (Python 2) — chuẩn Python 3.
- `.get(ch, 0)` trả về 0 nếu ký tự chưa có trong dict.
- `.items()` duyệt cặp (ký tự, số lần) theo thứ tự chèn.

### Ví dụ chạy thử (input → output)

**Input:**
```
abcdefgabc
```

**Output:**
```
a,2
b,2
c,2
d,1
e,1
f,1
g,1
```

### Lưu ý / mở rộng

Dùng `collections.Counter(s)` — một dòng, chuyên cho bài đếm tần suất:

```python
from collections import Counter
for ch, count in Counter(s).items():
    print(f"{ch},{count}")
```

---

## Câu 97 - Level 1

### Đề bài (tóm tắt tiếng Việt)

Nhập chuỗi từ bàn phím và **in ngược** chuỗi đó.

**Ví dụ:** `rise to vote sir` → `ris etov ot esir`

### Phân tích ý tưởng

Dùng cú pháp slice `[::-1]` — duyệt chuỗi với bước -1 (từ cuối về đầu).

**Độ phức tạp:** O(n).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
s = input("Nhập chuỗi: ")
print(s[::-1])
```

### Giải thích code từng phần

- `[::-1]` nghĩa là: bắt đầu cuối, kết thúc đầu, bước -1.
- Hoạt động với mọi sequence (str, list, tuple).

### Ví dụ chạy thử (input → output)

**Input:**
```
rise to vote sir
```

**Output:**
```
ris etov ot esir
```

### Lưu ý / mở rộng

- `reversed(s)` trả về iterator; cần `''.join(reversed(s))`.
- Slice `[::-1]` là cách phổ biến nhất trong Python.

---

## Câu 98 - Level 1

### Đề bài (tóm tắt tiếng Việt)

Nhập chuỗi từ bàn phím và in các ký tự ở **vị trí chỉ số chẵn** (0, 2, 4, ...).

**Ví dụ:** `H1e2l3l4o5w6o7r8l9d` → `Helloworld`

### Phân tích ý tưởng

Slice `[::2]` — lấy phần tử từ đầu đến cuối, bước nhảy 2 → chỉ số 0, 2, 4, ...

**Độ phức tạp:** O(n).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
s = input("Nhập chuỗi: ")
print(s[::2])
```

### Giải thích code từng phần

- `s[::2]` tương đương `s[0] + s[2] + s[4] + ...`
- Bỏ qua ký tự ở vị trí lẻ (1, 3, 5, ...) — trong ví dụ là các chữ số.

### Ví dụ chạy thử (input → output)

**Input:**
```
H1e2l3l4o5w6o7r8l9d
```

**Output:**
```
Helloworld
```

### Lưu ý / mở rộng

Tương đương: `''.join(s[i] for i in range(0, len(s), 2))` — dài hơn nhưng dễ tùy biến điều kiện.

---

## Câu 99 - Level 2

### Đề bài (tóm tắt tiếng Việt)

In **tất cả hoán vị** của list `[1, 2, 3]`.

### Phân tích ý tưởng

Dùng `itertools.permutations()` — sinh mọi cách sắp xếp các phần tử.

Với 3 phần tử: 3! = **6** hoán vị.

**Độ phức tạp:** O(n! × n).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
import itertools

perms = list(itertools.permutations([1, 2, 3]))
print(perms)
```

### Giải thích code từng phần

- `permutations(iterable)` trả về iterator các tuple hoán vị.
- Mỗi hoán vị là tuple (không phải list).
- `list(...)` gom hết 6 hoán vị để in.

### Ví dụ chạy thử (input → output)

```
[(1, 2, 3), (1, 3, 2), (2, 1, 3), (2, 3, 1), (3, 1, 2), (3, 2, 1)]
```

### Lưu ý / mở rộng

In từng hoán vị trên một dòng:

```python
for p in itertools.permutations([1, 2, 3]):
    print(p)
```

Tự cài đặt bằng đệ quy (backtracking) để hiểu sâu thuật toán.

---

## Câu 100 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Giải câu đố cổ Trung Quốc: Trong chuồng có **gà và thỏ**, tổng **35 đầu** và **94 chân**. Hỏi có bao nhiêu con gà và bao nhiêu con thỏ?

**Gợi ý:** Gà 2 chân, thỏ 4 chân.

### Phân tích ý tưởng

Gọi:
- `i` = số gà (2 chân)
- `j` = số thỏ (4 chân)

Hệ phương trình:
- `i + j = 35` (tổng đầu)
- `2i + 4j = 94` (tổng chân)

**Cách 1 — vòng lặp:** Thử mọi `i` từ 0 đến 35, tính `j = 35 - i`, kiểm tra `2i + 4j == 94`.

**Cách 2 — đại số:**
- Từ (1): `j = 35 - i`
- Thế vào (2): `2i + 4(35-i) = 94` → `140 - 2i = 94` → `i = 23`, `j = 12`

**Độ phức tạp:** O(n) với n = số đầu (35); đại số O(1).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def solve_chicken_rabbit(num_heads, num_legs):
    """Trả về (số_gà, số_thỏ) hoặc thông báo không có nghiệm."""
    for chickens in range(num_heads + 1):
        rabbits = num_heads - chickens
        if 2 * chickens + 4 * rabbits == num_legs:
            return chickens, rabbits
    return None


num_heads = 35
num_legs = 94
result = solve_chicken_rabbit(num_heads, num_legs)

if result:
    chickens, rabbits = result
    print(f"Gà: {chickens}, Thỏ: {rabbits}")
else:
    print("Không có nghiệm nguyên không âm.")
```

### Giải thích code từng phần

- `chickens` chạy từ 0 đến 35 — mọi cách chia đầu.
- `rabbits = num_heads - chickens` — số thỏ suy ra từ tổng đầu.
- Kiểm tra tổng chân: gà đóng góp 2, thỏ đóng góp 4.
- Tìm thấy `chickens=23`, `rabbits=12`: `2×23 + 4×12 = 46 + 48 = 94` ✓

### Ví dụ chạy thử (input → output)

```
Gà: 23, Thỏ: 12
```

Kiểm tra: 23 + 12 = 35 đầu; 23×2 + 12×4 = 46 + 48 = 94 chân.

### Lưu ý / mở rộng

**Công thức trực tiếp** (nhanh hơn vòng lặp):

```python
rabbits = (num_legs - 2 * num_heads) // 2
chickens = num_heads - rabbits
```

Điều kiện: `num_legs` chẵn, `num_legs >= 2*num_heads`, và nghiệm không âm.

---

*Tài liệu hoàn thành: 25 câu (Question 76 – Question 100).*
