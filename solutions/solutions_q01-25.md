# Lời giải chi tiết Python - Câu 1 đến Câu 25

Tài liệu này giải thích từng bài tập trong bộ *100+ Python challenging programming exercises for Python 3*.

---

## Câu 1 - Level 1

### Đề bài (tóm tắt tiếng Việt)

Viết chương trình tìm tất cả các số trong khoảng **2000 đến 3200** (bao gồm cả hai đầu) thỏa mãn:
- Chia hết cho **7**
- **Không** chia hết cho **5**

In kết quả trên **một dòng**, các số cách nhau bởi dấu phẩy.

### Phân tích ý tưởng

1. Duyệt từng số `i` trong khoảng `[2000, 3200]`.
2. Kiểm tra điều kiện: `i % 7 == 0` và `i % 5 != 0`.
3. Gom các số thỏa mãn vào danh sách, rồi nối bằng `','.join()`.

**Độ phức tạp:** O(n) với n = 1201 số cần duyệt — rất nhỏ, chấp nhận được.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
# Cách 1: dùng vòng lặp (dễ hiểu)
result = []
for i in range(2000, 3201):  # 3201 vì range không bao gồm điểm cuối
    if i % 7 == 0 and i % 5 != 0:
        result.append(str(i))

print(','.join(result))

# Cách 2: list comprehension (ngắn gọn, idiomatic Python)
# print(','.join(str(i) for i in range(2000, 3201) if i % 7 == 0 and i % 5 != 0))
```

### Giải thích code từng phần

- `range(2000, 3201)`: tạo dãy số từ 2000 đến 3200.
- `i % 7 == 0`: kiểm tra chia hết cho 7 (phần dư bằng 0).
- `i % 5 != 0`: loại các bội số của 5 (ví dụ 2030 chia hết cho cả 7 và 5).
- `str(i)`: chuyển số sang chuỗi để `join` nối được.
- `','.join(...)`: ghép các phần tử thành một chuỗi, phân cách bằng dấu phẩy.

### Ví dụ chạy thử (input → output)

Không cần nhập từ bàn phím. Chạy chương trình sẽ in (rút gọn đầu/cuối):

```
2002,2003,2009,2016,2023,...,3195,3197
```

### Lưu ý / mở rộng

- Có thể dùng list comprehension một dòng thay vòng `for` — ngắn hơn, cùng logic.
- Toán tử `%` (modulo) là công cụ cơ bản để kiểm tra chia hết.

---

## Câu 2 - Level 1

### Đề bài (tóm tắt tiếng Việt)

Viết chương trình tính **giai thừa** của một số nguyên nhập từ bàn phím và in kết quả.

Ví dụ: nhập `8` → in `40320` (vì 8! = 40320).

### Phân tích ý tưởng

Giai thừa: n! = 1 × 2 × 3 × ... × n, quy ước 0! = 1.

Có hai hướng:
1. **Đệ quy:** n! = n × (n-1)!
2. **Vòng lặp:** nhân dồn từ 1 đến n

**Độ phức tạp:** O(n) về số phép nhân.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def factorial(n: int) -> int:
  """Tính giai thừa bằng đệ quy."""
  if n <= 1:
    return 1
  return n * factorial(n - 1)


def factorial_iter(n: int) -> int:
  """Tính giai thừa bằng vòng lặp (tránh giới hạn đệ quy sâu)."""
  result = 1
  for i in range(2, n + 1):
    result *= i
  return result


if __name__ == "__main__":
  x = int(input())
  print(factorial(x))
  # Hoặc: print(math.factorial(x))  # dùng thư viện chuẩn
```

### Giải thích code từng phần

- `int(input())`: đọc và chuyển chuỗi nhập thành số nguyên.
- Điều kiện dừng đệ quy: `n <= 1` trả về 1.
- `factorial_iter`: an toàn hơn với n lớn vì Python giới hạn độ sâu đệ quy.

### Ví dụ chạy thử (input → output)

```
Input:  8
Output: 40320

Input:  0
Output: 1

Input:  5
Output: 120
```

### Lưu ý / mở rộng

- Python có sẵn `math.factorial(n)` — nên dùng trong thực tế.
- Với n rất lớn, kết quả tăng cực nhanh; cần kiểu `int` (Python hỗ trợ số nguyên lớn tùy ý).

---

## Câu 3 - Level 1

### Đề bài (tóm tắt tiếng Việt)

Cho số nguyên `n`, tạo **dictionary** chứa cặp `(i, i²)` với `i` từ 1 đến `n` (bao gồm cả hai đầu), rồi in dictionary.

Ví dụ: nhập `8` → `{1: 1, 2: 4, ..., 8: 64}`.

### Phân tích ý tưởng

1. Đọc `n`.
2. Duyệt `i` từ 1 đến n, gán `d[i] = i ** 2`.
3. In dictionary.

**Độ phức tạp:** O(n).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
n = int(input())

# Cách 1: vòng lặp
squares = {}
for i in range(1, n + 1):
  squares[i] = i ** 2

print(squares)

# Cách 2: dict comprehension (ngắn gọn)
# squares = {i: i ** 2 for i in range(1, n + 1)}
# print(squares)
```

### Giải thích code từng phần

- `range(1, n + 1)`: từ 1 đến n.
- `i ** 2`: lũy thừa bậc 2 (bình phương).
- Dictionary lưu cặp khóa-giá trị; khóa là số `i`, giá trị là `i²`.

### Ví dụ chạy thử (input → output)

```
Input:  8
Output: {1: 1, 2: 4, 3: 9, 4: 16, 5: 25, 6: 36, 7: 49, 8: 64}

Input:  3
Output: {1: 1, 2: 4, 3: 9}
```

### Lưu ý / mở rộng

- Dict comprehension `{i: i**2 for i in range(1, n+1)}` là cách Pythonic nhất.
- Có thể dùng `enumerate` nếu cần chỉ số phức tạp hơn.

---

## Câu 4 - Level 1

### Đề bài (tóm tắt tiếng Việt)

Nhập một chuỗi các số cách nhau bởi dấu phẩy, tạo **list** và **tuple** chứa từng phần tử (dạng chuỗi), rồi in cả hai.

Ví dụ: `34,67,55,33,12,98` → in list và tuple tương ứng.

### Phân tích ý tưởng

1. Đọc chuỗi đầu vào.
2. `split(',')` để tách thành list các chuỗi con.
3. `tuple(list)` để chuyển list sang tuple.

**Độ phức tạp:** O(n) với n là số phần tử.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
values = input().strip()
numbers_list = values.split(",")

# Tuple bất biến — tạo từ list
numbers_tuple = tuple(numbers_list)

print(numbers_list)
print(numbers_tuple)
```

### Giải thích code từng phần

- `strip()`: loại khoảng trắng thừa đầu/cuối (phòng người dùng gõ thừa space).
- `split(",")`: tách theo dấu phẩy → list các chuỗi.
- Đề bài yêu cầu giữ dạng **chuỗi** (`'34'`), không ép kiểu `int`.
- Tuple không thể thay đổi sau khi tạo (immutable).

### Ví dụ chạy thử (input → output)

```
Input:  34,67,55,33,12,98
Output:
['34', '67', '55', '33', '12', '98']
('34', '67', '55', '33', '12', '98')
```

### Lưu ý / mở rộng

- Nếu cần số nguyên: `[int(x) for x in numbers_list]`.
- List có thể sửa phần tử; tuple thì không.

---

## Câu 5 - Level 1

### Đề bài (tóm tắt tiếng Việt)

Định nghĩa class có ít nhất hai phương thức:
- `getString`: nhận chuỗi từ bàn phím
- `printString`: in chuỗi đó dạng **CHỮ HOA**

Kèm hàm test đơn giản.

### Phân tích ý tưởng

1. Tạo class với thuộc tính lưu chuỗi (`self.s`).
2. `getString` gọi `input()` gán vào `self.s`.
3. `printString` in `self.s.upper()`.
4. Hàm test tạo đối tượng và kiểm tra hành vi.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
class InputOutString:
  """Class nhận chuỗi từ console và in ra dạng chữ hoa."""

  def __init__(self):
    self.s = ""

  def getString(self):
    self.s = input()

  def printString(self):
    print(self.s.upper())


def test_input_out_string():
  """Test đơn giản — có thể mở rộng bằng unittest."""
  obj = InputOutString()
  obj.s = "hello python"  # gán trực tiếp để test không cần nhập tay
  assert obj.s.upper() == "HELLO PYTHON"
  print("Test passed!")


if __name__ == "__main__":
  test_input_out_string()
  str_obj = InputOutString()
  str_obj.getString()
  str_obj.printString()
```

### Giải thích code từng phần

- `__init__`: hàm khởi tạo, gán `self.s = ""`.
- `self`: tham chiếu đến chính đối tượng hiện tại.
- `.upper()`: phương thức chuỗi chuyển sang chữ hoa.
- Hàm test gán `obj.s` trực tiếp để kiểm tra logic mà không phụ thuộc input tương tác.

### Ví dụ chạy thử (input → output)

```
Input:  hello world
Output:
Test passed!
HELLO WORLD
```

### Lưu ý / mở rộng

- Nên dùng `unittest` hoặc `pytest` cho test chuyên nghiệp.
- Có thể gộp `getString` và `printString` thành một phương thức nếu muốn API gọn hơn.

---

## Câu 6 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Tính giá trị theo công thức:

**Q = √[(2 × C × D) / H]**

Trong đó C = 50, H = 30 cố định; D là các giá trị nhập (cách nhau bởi dấu phẩy). In kết quả làm tròn số nguyên gần nhất, cách nhau bởi dấu phẩy.

Ví dụ: `100,150,180` → `18,22,24`.

### Phân tích ý tưởng

1. Tách chuỗi D thành danh sách.
2. Với mỗi D: tính `sqrt(2 * C * D / H)`.
3. Làm tròn bằng `round()` rồi ép `int`.
4. Nối kết quả bằng dấu phẩy.

**Độ phức tạp:** O(k) với k là số giá trị D.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
import math

C = 50
H = 30

items = input().split(",")
results = []

for d_str in items:
  d = float(d_str.strip())
  q = math.sqrt(2 * C * d / H)
  results.append(str(int(round(q))))

print(",".join(results))
```

### Giải thích code từng phần

- `math.sqrt()`: căn bậc hai chính xác hơn `** 0.5` về mặt ý nghĩa toán học.
- `float(d_str)`: D có thể là số thực.
- `round(q)`: làm tròn đến số nguyên gần nhất (0.5 làm tròn về số chẵn trong Python 3).
- `int(...)`: đảm bảo in dạng số nguyên, không có `.0`.

### Ví dụ chạy thử (input → output)

```
Input:  100,150,180
Output: 18,22,24

Giải thích nhanh:
- D=100: sqrt(2*50*100/30) = sqrt(333.33...) ≈ 18.26 → 18
- D=150: ≈ 22.36 → 22
- D=180: ≈ 24.49 → 24
```

### Lưu ý / mở rộng

- Có thể viết gọn: `",".join(str(int(round(math.sqrt(2*C*float(d)/H)))) for d in input().split(","))`.
- Cẩn thận khi D = 0 hoặc âm — căn không xác định trong số thực.

---

## Câu 7 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Nhập hai số X, Y (cách nhau bởi dấu phẩy), tạo ma trận 2 chiều kích thước X×Y. Phần tử tại hàng `i`, cột `j` bằng `i * j` (i, j bắt đầu từ 0).

Ví dụ: `3,5` → `[[0,0,0,0,0], [0,1,2,3,4], [0,2,4,6,8]]`.

### Phân tích ý tưởng

1. Đọc X (số hàng), Y (số cột).
2. Khởi tạo ma trận toàn 0.
3. Gán `matrix[i][j] = i * j` bằng hai vòng lặp lồng nhau.

**Độ phức tạp:** O(X × Y).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
row_num, col_num = map(int, input().split(","))

# List comprehension lồng nhau — tạo ma trận trực tiếp
matrix = [[i * j for j in range(col_num)] for i in range(row_num)]

print(matrix)
```

### Giải thích code từng phần

- `map(int, ...)`: chuyển hai chuỗi số thành int.
- List comprehension ngoài: mỗi hàng `i`.
- List comprehension trong: mỗi cột `j`, giá trị `i * j`.
- Hàng 0 luôn toàn 0 vì `0 * j = 0`.

### Ví dụ chạy thử (input → output)

```
Input:  3,5
Output: [[0, 0, 0, 0, 0], [0, 1, 2, 3, 4], [0, 2, 4, 6, 8]]

Input:  2,3
Output: [[0, 0, 0], [0, 1, 2]]
```

### Lưu ý / mở rộng

- Đây là bảng cửu chương "một chiều" theo hàng.
- Với ma trận lớn, có thể dùng `numpy.zeros` + vector hóa.

---

## Câu 8 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Nhập chuỗi các từ cách nhau bởi dấu phẩy, **sắp xếp alphabet** rồi in lại, vẫn phân cách bằng dấu phẩy.

Ví dụ: `without,hello,bag,world` → `bag,hello,without,world`.

### Phân tích ý tưởng

1. `split(',')` tách thành list.
2. `sort()` sắp xếp tại chỗ (theo thứ tự từ điển).
3. `','.join()` ghép lại.

**Độ phức tạp:** O(n log n) do sort.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
items = input().split(",")
items.sort()
print(",".join(items))

# Hoặc một dòng:
# print(",".join(sorted(input().split(","))))
```

### Giải thích code từng phần

- `sort()`: sắp xếp list tại chỗ, không tạo list mới.
- `sorted()`: trả về list mới đã sắp xếp — an toàn hơn nếu cần giữ list gốc.
- Thứ tự alphabet phân biệt hoa/thường (chữ hoa đứng trước chữ thường trong ASCII).

### Ví dụ chạy thử (input → output)

```
Input:  without,hello,bag,world
Output: bag,hello,without,world
```

### Lưu ý / mở rộng

- Sắp xếp không phân biệt hoa thường: `key=str.lower`.
- Nếu có khoảng trắng sau dấu phẩy, nên `.strip()` từng phần tử.

---

## Câu 9 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Nhập **nhiều dòng** văn bản; khi gặp **dòng trống** thì dừng. In từng dòng đã nhập ở dạng **CHỮ HOA**.

Ví dụ:
```
Hello world
Practice makes perfect
(dòng trống)
```
→ in `HELLO WORLD` và `PRACTICE MAKES PERFECT`.

### Phân tích ý tưởng

1. Đọc liên tục bằng `input()`.
2. Nếu chuỗi rỗng (`""`) → `break`.
3. Ngược lại, thêm `s.upper()` vào list.
4. In từng dòng.

**Độ phức tạp:** O(tổng độ dài các dòng).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
lines = []

while True:
  s = input()
  if not s:  # dòng trống → kết thúc nhập
    break
  lines.append(s.upper())

for sentence in lines:
  print(sentence)
```

### Giải thích code từng phần

- `if not s`: chuỗi rỗng được coi là `False` trong ngữ cảnh boolean.
- `s.upper()`: chuyển toàn bộ ký tự sang hoa.
- Vòng `while True` + `break` là mẫu đọc đến khi gặp điều kiện dừng.

### Ví dụ chạy thử (input → output)

```
Input:
Hello world
Practice makes perfect
<Enter dòng trống>

Output:
HELLO WORLD
PRACTICE MAKES PERFECT
```

### Lưu ý / mở rộng

- Có thể đọc từ `sys.stdin` nếu input từ file.
- `s.strip() == ""` nếu muốn coi dòng chỉ có space là dòng trống.

---

## Câu 10 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Nhập chuỗi các từ cách nhau bởi **khoảng trắng**. Loại **từ trùng lặp**, sắp xếp alphabet, in kết quả (cách nhau bởi space).

Ví dụ: `hello world and practice makes perfect and hello world again` → `again and hello makes perfect practice world`.

### Phân tích ý tưởng

1. `split()` tách theo khoảng trắng.
2. `set()` loại trùng (không giữ thứ tự).
3. `sorted()` sắp xếp alphabet.
4. `" ".join()` ghép lại.

**Độ phức tạp:** O(n log n).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
s = input()
words = s.split()

# set loại trùng, sorted sắp xếp
unique_sorted = sorted(set(words))

print(" ".join(unique_sorted))
```

### Giải thích code từng phần

- `split()` không tham số: tách theo mọi khoảng trắng, bỏ chuỗi rỗng.
- `set(words)`: mỗi từ chỉ xuất hiện một lần.
- `sorted(set(...))`: trả về list đã sắp xếp.

### Ví dụ chạy thử (input → output)

```
Input:  hello world and practice makes perfect and hello world again
Output: again and hello makes perfect practice world
```

### Lưu ý / mở rộng

- Nếu cần **giữ thứ tự xuất hiện đầu tiên** khi loại trùng: dùng `dict.fromkeys(words)` (Python 3.7+ giữ thứ tự chèn).

---

## Câu 11 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Nhập chuỗi các số **nhị phân 4 bit** (cách nhau bởi dấu phẩy). Kiểm tra số nào **chia hết cho 5** khi chuyển sang thập phân; in các số nhị phân thỏa mãn, cách nhau bởi dấu phẩy.

Ví dụ: `0100,0011,1010,1001` → `1010` (vì 1010₂ = 10₁₀ chia hết cho 5).

### Phân tích ý tưởng

1. Tách chuỗi nhị phân.
2. `int(p, 2)` chuyển nhị phân → thập phân.
3. Kiểm tra `% 5 == 0`.
4. In các chuỗi nhị phân gốc thỏa mãn.

**Độ phức tạp:** O(k) với k số nhị phân.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
items = input().split(",")
result = []

for binary_str in items:
  decimal_value = int(binary_str.strip(), 2)  # cơ số 2
  if decimal_value % 5 == 0:
    result.append(binary_str.strip())

print(",".join(result))
```

### Giải thích code từng phần

- `int(s, 2)`: parse chuỗi nhị phân; ví dụ `int("1010", 2) == 10`.
- Giữ nguyên chuỗi nhị phân gốc khi in (theo yêu cầu đề).
- `strip()`: loại space thừa quanh mỗi số.

### Ví dụ chạy thử (input → output)

```
Input:  0100,0011,1010,1001
Output: 1010

Giải thích:
- 0100₂ = 4  → không chia hết cho 5
- 0011₂ = 3  → không
- 1010₂ = 10 → chia hết cho 5 ✓
- 1001₂ = 9  → không
```

### Lưu ý / mở rộng

- Mẹo: số nhị phân chia hết cho 5 khi kết thúc bằng `0` hoặc `1010` pattern — nhưng cách tổng quát vẫn là chuyển sang decimal.
- Có thể dùng list comprehension gọn hơn.

---

## Câu 12 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Tìm tất cả số từ **1000 đến 3000** (bao gồm) sao cho **mỗi chữ số** đều là số **chẵn** (0, 2, 4, 6, 8). In trên một dòng, cách nhau bởi dấu phẩy.

### Phân tích ý tưởng

1. Duyệt từ 1000 đến 3000.
2. Chuyển số sang chuỗi, kiểm tra từng ký tự có phải chữ số chẵn.
3. Hoặc: `all(int(d) % 2 == 0 for d in str(i))`.

**Độ phức tạp:** O(n × s) với s = 4 chữ số.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def all_digits_even(n: int) -> bool:
  """Kiểm tra mọi chữ số của n đều chẵn."""
  return all(int(ch) % 2 == 0 for ch in str(n))


result = [str(i) for i in range(1000, 3001) if all_digits_even(i)]
print(",".join(result))
```

### Giải thích code từng phần

- `str(n)`: tách từng chữ số dễ hơn phép chia liên tiếp.
- `all(...)`: trả về True nếu mọi phần tử trong generator đều True.
- `int(ch) % 2 == 0`: chữ số chẵn.

### Ví dụ chạy thử (input → output)

Không cần input. Kết quả bắt đầu bằng:

```
2000,2002,2004,2006,2008,2020,2022,...
```

(Tất cả số 4 chữ số chỉ gồm 0,2,4,6,8 trong khoảng cho trước.)

### Lưu ý / mở rộng

- Có thể sinh trực tiếp từ tích Descartes các chữ số chẵn thay vì duyệt — hiệu quả hơn nếu khoảng lớn.
- Chữ số đầu của số 4 chữ số không thể là 0 (nhưng 2000 vẫn hợp lệ).

---

## Câu 13 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Nhập một câu, đếm số **chữ cái** và số **chữ số**, in theo format:

```
LETTERS <số>
DIGITS <số>
```

Ví dụ: `hello world! 123` → `LETTERS 10`, `DIGITS 3`.

### Phân tích ý tưởng

Duyệt từng ký tự:
- `c.isalpha()` → tăng đếm chữ cái
- `c.isdigit()` → tăng đếm chữ số
- Ký tự khác (space, `!`, ...) bỏ qua

**Độ phức tạp:** O(len(s)).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
s = input()
letters = 0
digits = 0

for c in s:
  if c.isalpha():
    letters += 1
  elif c.isdigit():
    digits += 1

print("LETTERS", letters)
print("DIGITS", digits)
```

### Giải thích code từng phần

- `isalpha()`: True với chữ cái Unicode (a-z, A-Z, và nhiều ký tự khác).
- `isdigit()`: True với ký tự số.
- Dùng hai biến đếm riêng thay vì dictionary — rõ ràng hơn cho bài đơn giản.

### Ví dụ chạy thử (input → output)

```
Input:  hello world! 123
Output:
LETTERS 10
DIGITS 3
```

### Lưu ý / mở rộng

- Có thể dùng `sum(c.isalpha() for c in s)` — functional style.
- `string.ascii_letters` nếu chỉ muốn đếm a-z A-Z.

---

## Câu 14 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Nhập câu, đếm số chữ **viết hoa** và **viết thường**, in:

```
UPPER CASE <số>
LOWER CASE <số>
```

Ví dụ: `Hello world!` → `UPPER CASE 1`, `LOWER CASE 9`.

### Phân tích ý tưởng

Duyệt từng ký tự:
- `c.isupper()` → chữ hoa
- `c.islower()` → chữ thường

**Độ phức tạp:** O(len(s)).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
s = input()
upper_count = 0
lower_count = 0

for c in s:
  if c.isupper():
    upper_count += 1
  elif c.islower():
    lower_count += 1

print("UPPER CASE", upper_count)
print("LOWER CASE", lower_count)
```

### Giải thích code từng phần

- `isupper()` / `islower()` chỉ True với chữ cái có phân biệt hoa/thường.
- Space, số, dấu câu không được đếm vào cả hai.

### Ví dụ chạy thử (input → output)

```
Input:  Hello world!
Output:
UPPER CASE 1
LOWER CASE 9
```

### Lưu ý / mở rộng

- Khác với Câu 13: ở đây phân loại theo **case**, không phải chữ vs số.
- Tiếng Việt có dấu vẫn được `islower()`/`isupper()` nhận diện đúng.

---

## Câu 15 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Cho chữ số `a` (một ký tự), tính: **a + aa + aaa + aaaa** (ghép chữ số, không phải lũy thừa).

Ví dụ: `a = 9` → 9 + 99 + 999 + 9999 = **11106**.

### Phân tích ý tưởng

1. Đọc `a` dạng chuỗi.
2. Tạo các số: `int(a)`, `int(a*2)`, `int(a*3)`, `int(a*4)` bằng lặp chuỗi.
3. Cộng lại.

**Độ phức tạp:** O(1) — chỉ 4 số cố định.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
a = input().strip()

total = sum(int(a * i) for i in range(1, 5))  # a*1, a*2, a*3, a*4
print(total)
```

### Giải thích code từng phần

- `a * i` với chuỗi: lặp chuỗi `i` lần — `"9" * 3` → `"999"`.
- `int(...)` chuyển sang số nguyên để cộng.
- `range(1, 5)` tạo i = 1, 2, 3, 4.

### Ví dụ chạy thử (input → output)

```
Input:  9
Output: 11106

Input:  2
Output: 2468   (2 + 22 + 222 + 2222)
```

### Lưu ý / mở rộng

- Công thức tổng quát n项: dùng vòng `for i in range(1, n+1): total += int(a*i)`.
- Không nhầm với dãy số học a + a×10 + a×110 + ... — ở đây là ghép chữ số theo đề.

---

## Câu 16 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Nhập dãy số cách nhau bởi dấu phẩy. Dùng **list comprehension** để xử lý các số **lẻ** trong list.

> **Lưu ý:** Đề gốc ghi "square each odd number" nhưng output mẫu là `1,3,5,7,9` (giữ số lẻ, **không** bình phương). Lời giải làm theo **output mẫu** của đề.

### Phân tích ý tưởng

1. Tách chuỗi thành list số.
2. Lọc số lẻ: `int(x) % 2 != 0`.
3. In lại, nối bằng dấu phẩy.

**Độ phức tạp:** O(n).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
values = input()
numbers = [x.strip() for x in values.split(",") if int(x) % 2 != 0]
print(",".join(numbers))

# Nếu đúng nghĩa "bình phương số lẻ":
# squared_odds = [str(int(x) ** 2) for x in values.split(",") if int(x) % 2 != 0]
# print(",".join(squared_odds))  # → 1,9,25,49,81 với input mẫu
```

### Giải thích code từng phần

- List comprehension: `[expr for x in iterable if điều_kiện]`.
- `int(x) % 2 != 0`: số lẻ.
- Giữ dạng chuỗi khi in để khớp format đề.

### Ví dụ chạy thử (input → output)

```
Input:  1,2,3,4,5,6,7,8,9
Output: 1,3,5,7,9
```

### Lưu ý / mở rộng

- Đề có thể sai chính tả ("square" thay vì "select/filter"). Luôn đối chiếu output mẫu.
- Nếu thực sự cần bình phương: `[str(int(x)**2) for x in ... if int(x)%2]`.

---

## Câu 17 - Level 2

### Đề bài (tóm tắt tiếng Việt)

Tính **số dư tài khoản** từ nhật ký giao dịch:
- `D <số>` = gửi tiền (cộng)
- `W <số>` = rút tiền (trừ)

Đọc đến khi gặp **dòng trống**, in số dư cuối.

Ví dụ:
```
D 300
D 300
W 200
D 100
<dòng trống>
```
→ `500`.

### Phân tích ý tưởng

1. Khởi tạo `balance = 0`.
2. Đọc từng dòng, parse loại giao dịch và số tiền.
3. Cộng/trừ tương ứng.
4. In balance.

**Độ phức tạp:** O(số giao dịch).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
balance = 0

while True:
  line = input()
  if not line:
    break

  operation, amount_str = line.split()
  amount = int(amount_str)

  if operation == "D":
    balance += amount
  elif operation == "W":
    balance -= amount

print(balance)
```

### Giải thích code từng phần

- `line.split()`: tách theo khoảng trắng → `["D", "300"]`.
- `D` deposit, `W` withdraw — theo quy ước đề.
- Không xử lý rút quá số dư (đề không yêu cầu).

### Ví dụ chạy thử (input → output)

```
Input:
D 300
D 300
W 200
D 100

Output: 500

Tính: 0 + 300 + 300 - 200 + 100 = 500
```

### Lưu ý / mở rộng

- Có thể dùng `match/case` (Python 3.10+) thay `if/elif`.
- Thực tế nên kiểm tra số dư trước khi rút.

---

## Câu 18 - Level 3

### Đề bài (tóm tắt tiếng Việt)

Kiểm tra tính hợp lệ của **mật khẩu** theo tiêu chí:
1. Ít nhất 1 chữ thường [a-z]
2. Ít nhất 1 chữ hoa [A-Z]
3. Ít nhất 1 chữ số [0-9]
4. Ít nhất 1 ký tự đặc biệt trong `$#@`
5. Độ dài từ **6 đến 12** ký tự
6. Không chứa khoảng trắng

Nhập nhiều mật khẩu cách nhau bởi dấu phẩy; in các mật khẩu hợp lệ, cách nhau bởi dấu phẩy.

Ví dụ: `ABd1234@1,a F1#,2w3E*,2We3345` → `ABd1234@1`.

### Phân tích ý tưởng

Với mỗi mật khẩu, kiểm tra lần lượt tất cả điều kiện. Có thể dùng:
- Biểu thức chính quy (`re`)
- Hoặc duyệt ký tự + `any()`

**Độ phức tạp:** O(tổng độ dài các mật khẩu).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
import re


def is_valid_password(password: str) -> bool:
  """Trả về True nếu mật khẩu thỏa mọi tiêu chí."""
  if not (6 <= len(password) <= 12):
    return False
  if re.search(r"\s", password):  # có khoảng trắng
    return False
  if not re.search(r"[a-z]", password):
    return False
  if not re.search(r"[A-Z]", password):
    return False
  if not re.search(r"[0-9]", password):
    return False
  if not re.search(r"[$#@]", password):
    return False
  return True


passwords = input().split(",")
valid = [p for p in passwords if is_valid_password(p)]
print(",".join(valid))
```

### Giải thích code từng phần

- `re.search(pattern, s)`: tìm pattern trong chuỗi; trả về `None` nếu không có.
- `r"\s"`: khoảng trắng (space, tab, ...).
- Tách logic vào hàm `is_valid_password` — dễ test và đọc.
- List comprehension lọc mật khẩu hợp lệ.

### Ví dụ chạy thử (input → output)

```
Input:  ABd1234@1,a F1#,2w3E*,2We3345
Output: ABd1234@1

Phân tích:
- ABd1234@1: đủ hoa, thường, số, @, dài 9 → hợp lệ
- a F1#: có space → loại
- 2w3E*: thiếu ký tự $#@ → loại
- 2We3345: thiếu ký tự $#@ → loại
```

### Lưu ý / mở rộng

- Có thể gộp thành một regex dài — ngắn nhưng khó đọc.
- `r"^(?=.*[a-z])(?=.*[A-Z])..."` là kỹ thuật lookahead nâng cao.

---

## Câu 19 - Level 3

### Đề bài (tóm tắt tiếng Việt)

Nhập các bộ `(tên, tuổi, điểm/chiều cao)` dạng `Tom,19,80` (mỗi dòng một bộ). Dòng trống kết thúc nhập. Sắp xếp tăng dần theo thứ tự ưu tiên: **tên → tuổi → điểm**.

Ví dụ output: `[('John', '20', '90'), ('Jony', '17', '91'), ...]`.

### Phân tích ý tưởng

1. Đọc từng dòng, `split(",")` → tuple 3 phần tử.
2. `sorted(list, key=...)` với khóa nhiều cấp.
3. Dùng `operator.itemgetter(0, 1, 2)` hoặc lambda.

**Độ phức tạp:** O(n log n).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
from operator import itemgetter

records = []

while True:
  line = input()
  if not line:
    break
  records.append(tuple(line.split(",")))

# Sắp xếp theo tên, rồi tuổi, rồi cột thứ 3
sorted_records = sorted(records, key=itemgetter(0, 1, 2))
print(sorted_records)
```

### Giải thích code từng phần

- `tuple(...)`: bất biến, phù hợp bản ghi cố định.
- `itemgetter(0, 1, 2)`: tạo hàm trả về `(phần_tử_0, phần_tử_1, phần_tử_2)` để so sánh.
- Python so sánh tuple theo từng thành phần trái sang phải — đúng thứ tự ưu tiên đề bài.
- Dữ liệu giữ dạng **chuỗi** như đề mẫu (`'20'` không phải `20`).

### Ví dụ chạy thử (input → output)

```
Input:
Tom,19,80
John,20,90
Jony,17,91
Jony,17,93
Json,21,85

Output:
[('John', '20', '90'), ('Jony', '17', '91'), ('Jony', '17', '93'), ('Json', '21', '85'), ('Tom', '19', '80')]
```

### Lưu ý / mở rộng

- Nếu tuổi/điểm cần so sánh số: `key=lambda t: (t[0], int(t[1]), int(t[2]))`.
- `records.sort(key=itemgetter(0,1,2))` sắp xếp tại chỗ.

---

## Câu 20 - Level 3

### Đề bài (tóm tắt tiếng Việt)

Định nghĩa class (hoặc hàm) có **generator** duyệt các số **chia hết cho 7** trong khoảng **0 đến n** (n cho trước).

> **Lưu ý:** Solution gốc trong đề có lỗi (`reverse(100)` không tồn tại). Lời giải dưới đây sửa đúng yêu cầu.

### Phân tích ý tưởng

Dùng `yield` để trả từng giá trị mà không tạo list toàn bộ trong bộ nhớ:
- Duyệt `i` từ 0 đến n-1 (hoặc 0..n tùy cách hiểu "between 0 and n")
- Khi `i % 7 == 0` → `yield i`

**Độ phức tạp:** O(n) thời gian, O(1) bộ nhớ phụ (generator).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
class DivisibleBySeven:
  """Class bọc generator số chia hết cho 7 trong [0, n)."""

  def __init__(self, n: int):
    self.n = n

  def generate(self):
    for i in range(self.n):
      if i % 7 == 0:
        yield i


def put_numbers(n: int):
  """Hàm generator độc lập (theo tên trong đề gốc)."""
  for i in range(n):
    if i % 7 == 0:
      yield i


if __name__ == "__main__":
  n = 100
  gen = put_numbers(n)
  for value in gen:
    print(value, end=" ")
  # Output: 0 7 14 21 28 35 42 49 56 63 70 77 84 91 98
```

### Giải thích code từng phần

- `yield`: tạm dừng hàm, trả giá trị; lần gọi sau tiếp tục từ chỗ dừng.
- Generator **lazy**: chỉ tính khi cần — tiết kiệm bộ nhớ.
- `range(n)` → 0, 1, ..., n-1; số chia hết cho 7 đầu tiên là 0.

### Ví dụ chạy thử (input → output)

```
n = 30
Output: 0 7 14 21 28

n = 15
Output: 0 7 14
```

### Lưu ý / mở rộng

- Có thể dùng `range(0, n, 7)` thay generator — đơn giản hơn nhưng không học `yield`.
- Generator phù hợp luồng dữ liệu lớn hoặc vô hạn.

---

## Câu 21 - Level 3

### Đề bài (tóm tắt tiếng Việt)

Robot bắt đầu tại (0, 0), di chuyển theo lệnh:
- `UP k` / `DOWN k`: trục dọc (y)
- `LEFT k` / `RIGHT k`: trục ngang (x)

Đọc lệnh đến dòng trống. Tính **khoảng cách Euclidean** từ vị trí cuối về gốc, in số nguyên gần nhất.

Ví dụ: UP 5, DOWN 3, LEFT 3, RIGHT 2 → khoảng cách = 2.

### Phân tích ý tưởng

1. Theo dõi tọa độ `(x, y)` — theo solution gốc: index 0 là trục dọc (UP/DOWN), index 1 là ngang (LEFT/RIGHT).
2. Cập nhật sau mỗi lệnh.
3. Khoảng cách: `sqrt(x² + y²)`, làm tròn `int(round(...))`.

**Độ phức tạp:** O(số lệnh).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
import math

# pos[0]: trục dọc (UP/DOWN), pos[1]: trục ngang (LEFT/RIGHT)
pos = [0, 0]

while True:
  line = input()
  if not line:
    break

  direction, steps_str = line.split()
  steps = int(steps_str)

  if direction == "UP":
    pos[0] += steps
  elif direction == "DOWN":
    pos[0] -= steps
  elif direction == "LEFT":
    pos[1] -= steps
  elif direction == "RIGHT":
    pos[1] += steps

distance = math.sqrt(pos[0] ** 2 + pos[1] ** 2)
print(int(round(distance)))
```

### Giải thích code từng phần

- Ví dụ mẫu: UP 5 → y=5; DOWN 3 → y=2; LEFT 3 → x=-3; RIGHT 2 → x=-1.
- Khoảng cách: √(2² + (-1)²) = √5 ≈ 2.236 → làm tròn 2.
- Dùng list `pos` để cập nhật tại chỗ (có thể dùng tuple unpacking với biến x, y rõ hơn).

### Ví dụ chạy thử (input → output)

```
Input:
UP 5
DOWN 3
LEFT 3
RIGHT 2

Output: 2
```

### Lưu ý / mở rộng

- Nên đặt tên `x, y` thay `pos[0], pos[1]` cho dễ đọc.
- `math.hypot(x, y)` tính √(x²+y²) — tránh tràn số với giá trị lớn.

---

## Câu 22 - Level 3

### Đề bài (tóm tắt tiếng Việt)

Đếm **tần suất** mỗi từ trong câu nhập từ console. In theo thứ tự **alphabet** của từ: `từ:số_lần_xuất_hiện` mỗi dòng.

### Phân tích ý tưởng

1. `split()` tách từ.
2. Dùng dictionary đếm: `freq[word] = freq.get(word, 0) + 1`.
3. Sắp xếp khóa alphabet, in từng dòng.

**Độ phức tạp:** O(n + k log k) với k số từ khác nhau.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
from collections import Counter

line = input()
words = line.split()

# Cách 1: Counter (ngắn gọn, chuẩn Python)
freq = Counter(words)

for word in sorted(freq):
  print(f"{word}:{freq[word]}")

# Cách 2: dict thủ công
# freq = {}
# for word in words:
#   freq[word] = freq.get(word, 0) + 1
# for w in sorted(freq):
#   print(f"{w}:{freq[w]}")
```

### Giải thích code từng phần

- `Counter`: lớp chuyên đếm, nhận iterable từ.
- `sorted(freq)`: sắp xếp các khóa (từ).
- `freq.get(word, 0)`: lấy giá trị, mặc định 0 nếu chưa có.

### Ví dụ chạy thử (input → output)

```
Input:  New to Python or choosing between Python 2 and Python 3? Read Python 2 or Python 3.

Output:
2:2
3.:1
3?:1
New:1
Python:5
Read:1
and:1
between:1
choosing:1
or:2
to:1
```

### Lưu ý / mở rộng

- Phân biệt hoa/thường: `Python` ≠ `python`.
- `re.findall(r"\w+", line)` nếu muốn tách từ “sạch” hơn.

---

## Câu 23 - Level 1

### Đề bài (tóm tắt tiếng Việt)

Viết **hàm** tính **bình phương** của một số.

### Phân tích ý tưởng

Hàm nhận số, trả về `num ** 2` (toán tử lũy thừa Python).

**Độ phức tạp:** O(1).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def square(num):
  """Trả về bình phương của num."""
  return num ** 2


if __name__ == "__main__":
  print(square(2))   # 4
  print(square(3))   # 9
  print(square(-4))  # 16
```

### Giải thích code từng phần

- `def`: định nghĩa hàm.
- `** 2`: lũy thừa bậc 2; tương đương `num * num` với số nguyên.
- `return`: trả kết quả cho caller.

### Ví dụ chạy thử (input → output)

```
square(2)  → 4
square(3)  → 9
square(2.5) → 6.25
```

### Lưu ý / mở rộng

- `pow(num, 2)` cũng được.
- Type hint: `def square(num: float) -> float:`.

---

## Câu 24 - Level 1

### Đề bài (tóm tắt tiếng Việt)

In **tài liệu (docstring)** của một số hàm built-in Python (`abs`, `int`, `input`...) và thêm docstring cho hàm tự viết.

> Python 3 dùng `input()` thay `raw_input()` của Python 2.

### Phân tích ý tưởng

Mọi hàm/object Python có thuộc tính `__doc__` chứa chuỗi mô tả. Hàm tự định nghĩa dùng docstring ngay sau dòng `def`.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
# In docstring của hàm built-in
print("=== abs ===")
print(abs.__doc__)
print()

print("=== int ===")
print(int.__doc__)
print()

print("=== input ===")
print(input.__doc__)
print()


def square(num):
  """Return the square value of the input number.

  The input number can be int or float.
  """
  return num ** 2


print("=== square (hàm tự viết) ===")
print(square(2))
print(square.__doc__)
```

### Giải thích code từng phần

- `__doc__`: thuộc tính đặc biệt (dunder) lưu documentation.
- Docstring đặt trong `"""..."""` ngay dưới `def` — Python gán tự động cho `__doc__`.
- `help(abs)` mở trình xem tài liệu tương tác (pager).

### Ví dụ chạy thử (input → output)

```
=== abs ===
Return the absolute value of the argument.
...

=== square (hàm tự viết) ===
4
Return the square value of the input number.
...
```

### Lưu ý / mở rộng

- `help()`: công cụ tra cứu tích hợp.
- Viết docstring theo chuẩn Google/NumPy cho dự án lớn.

---

## Câu 25 - Level 1

### Đề bài (tóm tắt tiếng Việt)

Định nghĩa class có:
- **Tham số class** (class attribute) — dùng chung cho mọi instance
- **Tham số instance** (instance attribute) — riêng từng đối tượng

### Phân tích ý tưởng

- Gán biến trong thân class (ngoài method) → class attribute.
- Gán `self.xxx` trong `__init__` → instance attribute.
- Truy cập: `ClassName.attr` hoặc `obj.attr` (instance có thể che class attribute nếu trùng tên).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
class Person:
  # Thuộc tính class — chung cho cả lớp
  species = "Person"

  def __init__(self, name=None):
    # Thuộc tính instance — riêng từng object
    self.name = name


if __name__ == "__main__":
  jeffrey = Person("Jeffrey")
  print(f"{Person.species} name is {jeffrey.name}")

  nico = Person()
  nico.name = "Nico"  # gán sau khi khởi tạo
  print(f"{Person.species} name is {nico.name}")
```

### Giải thích code từng phần

- `Person.species`: đọc thuộc tính class qua tên lớp.
- `self.name`: mỗi instance có `name` riêng.
- `Person("Jeffrey")`: truyền tham số vào `__init__`.
- `nico.name = "Nico"`: gán instance attribute sau khi tạo object.

### Ví dụ chạy thử (input → output)

```
Person name is Jeffrey
Person name is Nico
```

### Lưu ý / mở rộng

- Đừng nhầm class attribute mutable (list, dict) — dùng chung có thể gây bug.
- `jeffrey.species` vẫn truy cập được nhưng `Person.species` rõ ý hơn.
- Đề gốc dùng `name = "Person"` làm class parameter — tương đương `species` ở trên.

---

*Tài liệu hoàn thành: 25/25 câu (Question 1 – Question 25).*
