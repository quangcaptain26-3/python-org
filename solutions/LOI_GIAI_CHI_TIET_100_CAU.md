# Lời giải chi tiết - 100+ Python Challenging Exercises (Python 3)

> Tài liệu lời giải chi tiết bằng tiếng Việt cho toàn bộ 100 câu hỏi.
> Nguồn đề: `100+ Python challenging programming exercises for Python 3.md`
> Mỗi câu gồm: Đề bài | Phân tích | Code | Giải thích | Ví dụ | Lưu ý

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



---


## Câu 26 - Level 1

### Đề bài (tóm tắt tiếng Việt)
Định nghĩa một hàm nhận hai số và trả về tổng của chúng.

### Phân tích ý tưởng
- Đây là bài tập cơ bản về **định nghĩa hàm** trong Python.
- Hàm nhận hai tham số `a` và `b`, cộng chúng lại và `return` kết quả.
- Độ phức tạp: **O(1)** — chỉ thực hiện một phép cộng.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def sum_two_numbers(a, b):
    """Tính tổng hai số."""
    return a + b


if __name__ == "__main__":
    print(sum_two_numbers(1, 2))   # 3
    print(sum_two_numbers(10, 25)) # 35
```

### Giải thích code từng phần
- `def sum_two_numbers(a, b):` — khai báo hàm với hai tham số.
- `return a + b` — trả về tổng; dùng `return` thay vì chỉ `print` để hàm có thể tái sử dụng.
- Khối `if __name__ == "__main__":` — chỉ chạy khi file được thực thi trực tiếp, không chạy khi được import.

### Ví dụ chạy thử (input → output)
```
sum_two_numbers(1, 2)  →  3
sum_two_numbers(-5, 8) →  3
```

### Lưu ý / mở rộng
- Có thể dùng `operator.add(a, b)` hoặc `sum([a, b])` nhưng phép `+` là cách tự nhiên nhất.
- Nếu cần hỗ trợ nhiều số: `def sum_numbers(*args): return sum(args)`.

---

## Câu 27 - Level 1

### Đề bài (tóm tắt tiếng Việt)
Định nghĩa hàm nhận một số nguyên, chuyển sang chuỗi và in ra màn hình.

### Phân tích ý tưởng
- Dùng hàm tích hợp `str()` để ép kiểu số → chuỗi.
- In kết quả bằng `print()`.
- Độ phức tạp: **O(1)**.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def print_integer_as_string(n):
    """Chuyển số nguyên thành chuỗi và in ra."""
    print(str(n))


if __name__ == "__main__":
    print_integer_as_string(3)
```

### Giải thích code từng phần
- `str(n)` — chuyển số nguyên `n` thành chuỗi (ví dụ `3` → `"3"`).
- `print(str(n))` — in chuỗi ra console; `print(n)` cũng cho kết quả tương tự vì `print` tự gọi `str()`.

### Ví dụ chạy thử (input → output)
```
print_integer_as_string(3)   →  3
print_integer_as_string(0)   →  0
print_integer_as_string(-42) →  -42
```

### Lưu ý / mở rộng
- Câu 27 và 28 trong đề gốc giống nhau; đây là bài làm quen với ép kiểu.
- Có thể dùng f-string: `print(f"{n}")`.

---

## Câu 28 - Level 1

### Đề bài (tóm tắt tiếng Việt)
Giống Câu 27: định nghĩa hàm nhận số nguyên, chuyển sang chuỗi và in ra console.

### Phân tích ý tưởng
- Tương tự Câu 27; tập trung vào `str()` và `print()`.
- Có thể viết hàm trả về chuỗi thay vì chỉ in, linh hoạt hơn.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def integer_to_string(n):
    """Trả về biểu diễn chuỗi của số nguyên."""
    return str(n)


if __name__ == "__main__":
    result = integer_to_string(3)
    print(result)  # in ra: 3
```

### Giải thích code từng phần
- Hàm `integer_to_string` **trả về** chuỗi thay vì in trực tiếp — dễ test và tái sử dụng.
- `print(result)` — in kết quả ra màn hình theo yêu cầu đề.

### Ví dụ chạy thử (input → output)
```
integer_to_string(3) → "3" (in ra: 3)
integer_to_string(100) → "100"
```

### Lưu ý / mở rộng
- Phiên bản trả về chuỗi tốt hơn phiên bản chỉ `print` vì tách biệt logic và hiển thị.

---

## Câu 29 - Level 1

### Đề bài (tóm tắt tiếng Việt)
Định nghĩa hàm nhận hai chuỗi biểu diễn số nguyên, cộng chúng và in kết quả.

### Phân tích ý tưởng
- Dùng `int()` để chuyển chuỗi số → số nguyên.
- Cộng hai số và in kết quả.
- Độ phức tạp: **O(1)**.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def sum_string_integers(s1, s2):
    """Nhận hai chuỗi số, cộng và in tổng."""
    total = int(s1) + int(s2)
    print(total)


if __name__ == "__main__":
    sum_string_integers("3", "4")
```

### Giải thích code từng phần
- `int(s1)` — chuyển `"3"` thành số nguyên `3`.
- `int(s1) + int(s2)` — cộng hai số nguyên.
- `print(total)` — in kết quả ra console.

### Ví dụ chạy thử (input → output)
```
sum_string_integers("3", "4")   →  7
sum_string_integers("10", "-3") →  7
```

### Lưu ý / mở rộng
- Không dùng `s1 + s2` trực tiếp vì đó là **nối chuỗi** (`"3" + "4"` → `"34"`).
- Có thể mở rộng: `sum(int(x) for x in strings)`.

---

## Câu 30 - Level 1

### Đề bài (tóm tắt tiếng Việt)
Định nghĩa hàm nhận hai chuỗi, nối chúng lại và in kết quả.

### Phân tích ý tưởng
- Dùng toán tử `+` để nối chuỗi (concatenation).
- In chuỗi kết quả.
- Độ phức tạp: **O(n + m)** với n, m là độ dài hai chuỗi.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def concatenate_strings(s1, s2):
    """Nối hai chuỗi và in kết quả."""
    print(s1 + s2)


if __name__ == "__main__":
    concatenate_strings("3", "4")  # in ra: 34
```

### Giải thích code từng phần
- `s1 + s2` — nối hai chuỗi liên tiếp, không có khoảng trắng ở giữa.
- Khác với Câu 29: ở đây `"3" + "4"` = `"34"`, không phải `7`.

### Ví dụ chạy thử (input → output)
```
concatenate_strings("3", "4")      →  34
concatenate_strings("Hello", "World") →  HelloWorld
```

### Lưu ý / mở rộng
- Cách Pythonic hơn: `"".join([s1, s2])` hoặc f-string `f"{s1}{s2}"`.
- Nếu cần khoảng trắng: `f"{s1} {s2}"`.

---

## Câu 31 - Level 1

### Đề bài (tóm tắt tiếng Việt)
Định nghĩa hàm nhận hai chuỗi, in chuỗi dài hơn. Nếu bằng nhau về độ dài, in cả hai (mỗi chuỗi một dòng).

### Phân tích ý tưởng
- Dùng `len()` so sánh độ dài.
- Ba nhánh: dài hơn → in chuỗi dài; ngắn hơn → in chuỗi kia; bằng nhau → in cả hai.
- Độ phức tạp: **O(1)** (chỉ so sánh độ dài).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def print_longer_string(s1, s2):
    """In chuỗi dài hơn; nếu bằng nhau thì in cả hai."""
    if len(s1) > len(s2):
        print(s1)
    elif len(s2) > len(s1):
        print(s2)
    else:
        print(s1)
        print(s2)


if __name__ == "__main__":
    print_longer_string("one", "three")  # in: three
    print_longer_string("ab", "cd")      # in: ab \n cd
```

### Giải thích code từng phần
- `len(s1)`, `len(s2)` — lấy số ký tự của mỗi chuỗi.
- `if/elif/else` — xử lý ba trường hợp theo đề bài.
- Nhánh `else` in `s1` rồi `s2` trên hai dòng riêng.

### Ví dụ chạy thử (input → output)
```
print_longer_string("one", "three") →  three
print_longer_string("hi", "bye")    →  bye
print_longer_string("ab", "cd")     →  ab
                                      cd
```

### Lưu ý / mở rộng
- Có thể rút gọn: `for s in sorted([s1, s2], key=len, reverse=True)[:1 if len(s1)!=len(s2) else 2]` — nhưng dạng if/elif dễ đọc hơn.

---

## Câu 32 - Level 1

### Đề bài (tóm tắt tiếng Việt)
Định nghĩa hàm nhận số nguyên: nếu chẵn in `"It is an even number"`, nếu lẻ in `"It is an odd number"`.

### Phân tích ý tưởng
- Số chẵn khi `n % 2 == 0`.
- Dùng toán tử modulo `%` để lấy phần dư khi chia cho 2.
- Độ phức tạp: **O(1)**.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def check_even_odd(n):
    """Kiểm tra số chẵn hay lẻ và in thông báo."""
    if n % 2 == 0:
        print("It is an even number")
    else:
        print("It is an odd number")


if __name__ == "__main__":
    check_even_odd(7)  # It is an odd number
    check_even_odd(4)  # It is an even number
```

### Giải thích code từng phần
- `n % 2` — phần dư khi chia `n` cho 2; bằng 0 nghĩa là chẵn.
- Thông báo in đúng theo định dạng đề bài (tiếng Anh).

### Ví dụ chạy thử (input → output)
```
check_even_odd(7)  →  It is an odd number
check_even_odd(0)  →  It is an even number
check_even_odd(-3) →  It is an odd number
```

### Lưu ý / mở rộng
- Python 3: `n % 2 == 0` hoạt động đúng với số âm.
- Có thể dùng: `print("It is an even number" if n % 2 == 0 else "It is an odd number")`.

---

## Câu 33 - Level 1

### Đề bài (tóm tắt tiếng Việt)
Định nghĩa hàm in dictionary với key từ 1 đến 3, value là bình phương của key.

### Phân tích ý tưởng
- Tạo dict: `{1: 1, 2: 4, 3: 9}`.
- Gán từng cặp key-value hoặc dùng dict comprehension.
- Độ phức tạp: **O(1)** (chỉ 3 phần tử).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def print_square_dict():
    """In dict {key: key^2} với key từ 1 đến 3."""
    d = {i: i ** 2 for i in range(1, 4)}
    print(d)


if __name__ == "__main__":
    print_square_dict()
```

### Giải thích code từng phần
- `{i: i ** 2 for i in range(1, 4)}` — dict comprehension; `range(1, 4)` tạo 1, 2, 3.
- `i ** 2` — lũy thừa bậc 2 (bình phương).
- `print(d)` — in toàn bộ dictionary.

### Ví dụ chạy thử (input → output)
```
print_square_dict()  →  {1: 1, 2: 4, 3: 9}
```

### Lưu ý / mở rộng
- Cách thủ công: `d = {}; d[1]=1; d[2]=4; d[3]=9`.
- Dict comprehension gọn và dễ mở rộng sang Câu 34.

---

## Câu 34 - Level 1

### Đề bài (tóm tắt tiếng Việt)
Định nghĩa hàm in dictionary với key từ 1 đến 20, value là bình phương của key.

### Phân tích ý tưởng
- Mở rộng Câu 33 với `range(1, 21)`.
- Dùng vòng lặp hoặc dict comprehension.
- Độ phức tạp: **O(n)** với n = 20.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def print_square_dict():
    """In dict {i: i^2} với i từ 1 đến 20."""
    d = {i: i ** 2 for i in range(1, 21)}
    print(d)


if __name__ == "__main__":
    print_square_dict()
```

### Giải thích code từng phần
- `range(1, 21)` — số từ 1 đến 20 (21 không bao gồm).
- Dict comprehension tạo 20 cặp key-value trong một dòng.
- Kết quả: `{1: 1, 2: 4, ..., 20: 400}`.

### Ví dụ chạy thử (input → output)
```
print_square_dict()  →  {1: 1, 2: 4, 3: 9, ..., 20: 400}
```

### Lưu ý / mở rộng
- Cách dùng vòng lặp:
  ```python
  d = {}
  for i in range(1, 21):
      d[i] = i ** 2
  ```

---

## Câu 35 - Level 1

### Đề bài (tóm tắt tiếng Việt)
Tạo dictionary key 1–20, value là bình phương key, nhưng **chỉ in các value** (không in key).

### Phân tích ý tưởng
- Tạo dict như Câu 34.
- Duyệt `.values()` hoặc `.items()` và chỉ in phần value.
- Độ phức tạp: **O(n)**.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def print_square_values():
    """Tạo dict bình phương 1-20, chỉ in các value."""
    d = {i: i ** 2 for i in range(1, 21)}
    for value in d.values():
        print(value)


if __name__ == "__main__":
    print_square_values()
```

### Giải thích code từng phần
- `d.values()` — trả về tập hợp các giá trị trong dict.
- Vòng `for` in từng value trên một dòng: 1, 4, 9, 16, ...

### Ví dụ chạy thử (input → output)
```
print_square_values()  →
1
4
9
...
400
```

### Lưu ý / mở rộng
- Có thể viết gọn: `[print(v) for v in (i**2 for i in range(1, 21))]` nhưng không nên lạm dụng list comprehension chỉ để side-effect.
- Hoặc: `print(*[i**2 for i in range(1, 21)], sep='\n')`.

---

## Câu 36 - Level 1

### Đề bài (tóm tắt tiếng Việt)
Tạo dictionary key 1–20, value là bình phương key, nhưng **chỉ in các key**.

### Phân tích ý tưởng
- Tương tự Câu 35 nhưng duyệt `.keys()` thay vì `.values()`.
- Độ phức tạp: **O(n)**.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def print_square_keys():
    """Tạo dict bình phương 1-20, chỉ in các key."""
    d = {i: i ** 2 for i in range(1, 21)}
    for key in d.keys():
        print(key)


if __name__ == "__main__":
    print_square_keys()
```

### Giải thích code từng phần
- `d.keys()` — lấy tất cả key của dictionary.
- In lần lượt: 1, 2, 3, ..., 20.

### Ví dụ chạy thử (input → output)
```
print_square_keys()  →
1
2
3
...
20
```

### Lưu ý / mở rộng
- Trong Python 3, `for key in d:` cũng duyệt key — không cần `.keys()` trừ khi muốn rõ ý định.
- Câu 35 và 36 giúp làm quen `.keys()`, `.values()`, `.items()`.

---

## Câu 37 - Level 1

### Đề bài (tóm tắt tiếng Việt)
Định nghĩa hàm tạo và in list chứa bình phương các số từ 1 đến 20.

### Phân tích ý tưởng
- Dùng list comprehension hoặc vòng lặp + `append`.
- Mỗi phần tử: `i ** 2` với i từ 1 đến 20.
- Độ phức tạp: **O(n)**.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def print_square_list():
    """Tạo và in list bình phương từ 1 đến 20."""
    squares = [i ** 2 for i in range(1, 21)]
    print(squares)


if __name__ == "__main__":
    print_square_list()
```

### Giải thích code từng phần
- List comprehension `[i ** 2 for i in range(1, 21)]` — tạo list trong một biểu thức.
- Kết quả: `[1, 4, 9, 16, ..., 400]`.

### Ví dụ chạy thử (input → output)
```
print_square_list()  →  [1, 4, 9, 16, 25, 36, 49, 64, 81, 100, 121, 144, 169, 196, 225, 256, 289, 324, 361, 400]
```

### Lưu ý / mở rộng
- Tương đương: `list(map(lambda x: x**2, range(1, 21)))`.

---

## Câu 38 - Level 1

### Đề bài (tóm tắt tiếng Việt)
Tạo list bình phương 1–20, sau đó **in 5 phần tử đầu tiên**.

### Phân tích ý tưởng
- Tạo list như Câu 37.
- Dùng slice `[:5]` lấy 5 phần tử đầu.
- Độ phức tạp: **O(n)** tạo list, **O(1)** slice (tham chiếu).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def print_first_five_squares():
    """In 5 phần tử đầu của list bình phương 1-20."""
    squares = [i ** 2 for i in range(1, 21)]
    print(squares[:5])


if __name__ == "__main__":
    print_first_five_squares()
```

### Giải thích code từng phần
- `squares[:5]` — slice từ index 0 đến 4 (5 phần tử).
- Cú pháp slice: `list[start:stop]` — `stop` không bao gồm.

### Ví dụ chạy thử (input → output)
```
print_first_five_squares()  →  [1, 4, 9, 16, 25]
```

### Lưu ý / mở rộng
- Có thể tạo trực tiếp: `[i**2 for i in range(1, 6)]` nếu chỉ cần 5 phần tử đầu.

---

## Câu 39 - Level 1

### Đề bài (tóm tắt tiếng Việt)
Tạo list bình phương 1–20, sau đó **in 5 phần tử cuối cùng**.

### Phân tích ý tưởng
- Slice âm `[-5:]` lấy 5 phần tử cuối.
- Độ phức tạp: **O(n)** tạo list.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def print_last_five_squares():
    """In 5 phần tử cuối của list bình phương 1-20."""
    squares = [i ** 2 for i in range(1, 21)]
    print(squares[-5:])


if __name__ == "__main__":
    print_last_five_squares()
```

### Giải thích code từng phần
- `squares[-5:]` — từ phần tử thứ 5 tính từ cuối đến hết list.
- Index âm: `-1` là phần tử cuối, `-5` là phần tử thứ 5 từ cuối.

### Ví dụ chạy thử (input → output)
```
print_last_five_squares()  →  [256, 289, 324, 361, 400]
```

### Lưu ý / mở rộng
- `squares[15:]` cũng cho cùng kết quả vì list có 20 phần tử (index 15–19).

---

## Câu 40 - Level 1

### Đề bài (tóm tắt tiếng Việt)
Tạo list bình phương 1–20, in **tất cả phần tử trừ 5 phần tử đầu**.

### Phân tích ý tưởng
- Slice `[5:]` — bỏ 5 phần tử đầu, lấy phần còn lại.
- Độ phức tạp: **O(n)**.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def print_squares_except_first_five():
    """In list bình phương 1-20, bỏ 5 phần tử đầu."""
    squares = [i ** 2 for i in range(1, 21)]
    print(squares[5:])


if __name__ == "__main__":
    print_squares_except_first_five()
```

### Giải thích code từng phần
- `squares[5:]` — từ index 5 đến hết (tức phần tử thứ 6 trở đi).
- Kết quả: 15 phần tử — bình phương của 6 đến 20.

### Ví dụ chạy thử (input → output)
```
print_squares_except_first_five()  →  [36, 49, 64, 81, 100, 121, 144, 169, 196, 225, 256, 289, 324, 361, 400]
```

### Lưu ý / mở rộng
- Solution gốc dùng `print li[5:]` (cú pháp Python 2); Python 3 cần `print(li[5:])`.

---

## Câu 41 - Level 1

### Đề bài (tóm tắt tiếng Việt)
Định nghĩa hàm tạo và in **tuple** chứa bình phương các số từ 1 đến 20.

### Phân tích ý tưởng
- Tạo list bình phương, chuyển sang tuple bằng `tuple()`.
- Hoặc dùng tuple comprehension: `tuple(i**2 for i in range(1, 21))`.
- Độ phức tạp: **O(n)**.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def print_square_tuple():
    """Tạo và in tuple bình phương từ 1 đến 20."""
    squares = tuple(i ** 2 for i in range(1, 21))
    print(squares)


if __name__ == "__main__":
    print_square_tuple()
```

### Giải thích code từng phần
- `tuple(i ** 2 for i in range(1, 21))` — generator expression bên trong `tuple()`.
- Tuple **bất biến** (immutable) — khác list có thể sửa phần tử.

### Ví dụ chạy thử (input → output)
```
print_square_tuple()  →  (1, 4, 9, 16, ..., 400)
```

### Lưu ý / mở rộng
- Cách qua list: `tuple([i**2 for i in range(1, 21)])`.
- Tuple phù hợp khi dữ liệu không cần thay đổi.

---

## Câu 42 - Level 1

### Đề bài (tóm tắt tiếng Việt)
Cho tuple `(1,2,3,4,5,6,7,8,9,10)`, in nửa đầu trên một dòng và nửa sau trên dòng khác.

### Phân tích ý tưởng
- Tuple có 10 phần tử → chia đôi: 5 phần tử đầu, 5 phần tử sau.
- Dùng slice `[:5]` và `[5:]`.
- Độ phức tạp: **O(1)** (slice tạo tuple con).

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def print_tuple_halves():
    """In nửa đầu và nửa sau của tuple cho sẵn."""
    tp = (1, 2, 3, 4, 5, 6, 7, 8, 9, 10)
    first_half = tp[:5]
    second_half = tp[5:]
    print(first_half)
    print(second_half)


if __name__ == "__main__":
    print_tuple_halves()
```

### Giải thích code từng phần
- `tp[:5]` → `(1, 2, 3, 4, 5)`.
- `tp[5:]` → `(6, 7, 8, 9, 10)`.
- Slice hoạt động giống trên list và tuple.

### Ví dụ chạy thử (input → output)
```
print_tuple_halves()  →
(1, 2, 3, 4, 5)
(6, 7, 8, 9, 10)
```

### Lưu ý / mở rộng
- Với tuple lẻ phần tử: `mid = len(tp) // 2` rồi `tp[:mid]`, `tp[mid:]`.

---

## Câu 43 - Level 1

### Đề bài (tóm tắt tiếng Việt)
Cho tuple `(1,2,3,4,5,6,7,8,9,10)`, tạo và in tuple mới chỉ gồm các số **chẵn**.

### Phân tích ý tưởng
- Duyệt từng phần tử, giữ lại nếu `i % 2 == 0`.
- Dùng list comprehension + `tuple()`, hoặc generator expression.
- Solution gốc có lỗi: dùng `tp[i]` trong vòng `for i in tp` — sai vì `i` là giá trị, không phải index.
- Độ phức tạp: **O(n)**.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def print_even_tuple():
    """Lọc số chẵn từ tuple cho sẵn."""
    tp = (1, 2, 3, 4, 5, 6, 7, 8, 9, 10)
    even_tp = tuple(x for x in tp if x % 2 == 0)
    print(even_tp)


if __name__ == "__main__":
    print_even_tuple()
```

### Giải thích code từng phần
- `for x in tp` — `x` lần lượt là 1, 2, 3, ... (giá trị phần tử).
- `if x % 2 == 0` — chỉ giữ số chẵn.
- `tuple(...)` — chuyển kết quả lọc thành tuple.

### Ví dụ chạy thử (input → output)
```
print_even_tuple()  →  (2, 4, 6, 8, 10)
```

### Lưu ý / mở rộng
- **Lỗi solution gốc:** `for i in tp: if tp[i]%2==0` — khi `i=2`, `tp[2]` là phần tử index 2 (=3), không phải kiểm tra `i`.
- Cách đúng: `tuple(x for x in tp if x % 2 == 0)`.

---

## Câu 44 - Level 1

### Đề bài (tóm tắt tiếng Việt)
Nhận chuỗi từ input: nếu là `"yes"`, `"YES"` hoặc `"Yes"` thì in `"Yes"`, ngược lại in `"No"`.

### Phân tích ý tưởng
- So sánh chuỗi với ba giá trị cụ thể.
- Có thể dùng `s in ("yes", "YES", "Yes")` hoặc `s.lower() == "yes"`.
- Độ phức tạp: **O(1)**.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def check_yes_no():
    """Đọc chuỗi từ console, in Yes hoặc No."""
    s = input()
    if s in ("yes", "YES", "Yes"):
        print("Yes")
    else:
        print("No")


if __name__ == "__main__":
    check_yes_no()
```

### Giải thích code từng phần
- `input()` — đọc một dòng từ console (Python 3; thay `raw_input` của Python 2).
- `s in (...)` — kiểm tra membership trong tuple các giá trị hợp lệ.
- In đúng `"Yes"` / `"No"` theo đề.

### Ví dụ chạy thử (input → output)
```
yes   →  Yes
YES   →  Yes
Yes   →  Yes
no    →  No
Maybe →  No
```

### Lưu ý / mở rộng
- Nếu chấp nhận mọi cách viết hoa/thường: `if s.lower() == "yes": print("Yes")`.
- Đề chỉ yêu cầu đúng 3 dạng cụ thể nên dùng `in` an toàn hơn.

---

## Câu 45 - Level 2

### Đề bài (tóm tắt tiếng Việt)
Dùng hàm `filter()` để lọc số chẵn từ list `[1,2,3,4,5,6,7,8,9,10]`.

### Phân tích ý tưởng
- `filter(function, iterable)` — giữ phần tử khi function trả về truthy.
- Dùng `lambda x: x % 2 == 0` làm điều kiện lọc.
- Python 3: `filter` trả về iterator → bọc `list()` để in.
- Độ phức tạp: **O(n)**.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def filter_even_numbers():
    """Lọc số chẵn bằng filter() và lambda."""
    numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    even_numbers = list(filter(lambda x: x % 2 == 0, numbers))
    print(even_numbers)


if __name__ == "__main__":
    filter_even_numbers()
```

### Giải thích code từng phần
- `lambda x: x % 2 == 0` — hàm ẩn danh, trả về `True` nếu `x` chẵn.
- `filter(...)` — lọc iterable theo điều kiện.
- `list(...)` — chuyển iterator thành list để hiển thị.

### Ví dụ chạy thử (input → output)
```
filter_even_numbers()  →  [2, 4, 6, 8, 10]
```

### Lưu ý / mở rộng
- Cách hiện đại tương đương: `[x for x in numbers if x % 2 == 0]`.
- Solution gốc in trực tiếp `filter(...)` → in `<filter object at 0x...>` trên Python 3.

---

## Câu 46 - Level 2

### Đề bài (tóm tắt tiếng Việt)
Dùng `map()` để tạo list bình phương các phần tử trong `[1,2,3,4,5,6,7,8,9,10]`.

### Phân tích ý tưởng
- `map(function, iterable)` — áp dụng function lên từng phần tử.
- `lambda x: x ** 2` — tính bình phương.
- Bọc `list()` vì Python 3 trả về map object.
- Độ phức tạp: **O(n)**.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def map_square_numbers():
    """Bình phương từng phần tử bằng map() và lambda."""
    numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    squared = list(map(lambda x: x ** 2, numbers))
    print(squared)


if __name__ == "__main__":
    map_square_numbers()
```

### Giải thích code từng phần
- `map(lambda x: x ** 2, numbers)` — áp dụng bình phương cho mỗi phần tử.
- `list(...)` — materialize kết quả thành list.

### Ví dụ chạy thử (input → output)
```
map_square_numbers()  →  [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

### Lưu ý / mở rộng
- Tương đương: `[x**2 for x in numbers]`.
- Có thể dùng `operator.mul` hoặc `pow(x, 2)` nhưng `x**2` rõ ràng nhất.

---

## Câu 47 - Level 2

### Đề bài (tóm tắt tiếng Việt)
Kết hợp `map()` và `filter()` để tạo list bình phương của **các số chẵn** trong `[1,2,3,4,5,6,7,8,9,10]`.

### Phân tích ý tưởng
- Bước 1: `filter` lấy số chẵn.
- Bước 2: `map` bình phương kết quả.
- Có thể lồng: `map(lambda x: x**2, filter(lambda x: x%2==0, li))`.
- Độ phức tạp: **O(n)**.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def map_filter_even_squares():
    """Bình phương các số chẵn: filter rồi map."""
    numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    result = list(map(lambda x: x ** 2, filter(lambda x: x % 2 == 0, numbers)))
    print(result)


if __name__ == "__main__":
    map_filter_even_squares()
```

### Giải thích code từng phần
- `filter(lambda x: x % 2 == 0, numbers)` — iterator các số chẵn: 2, 4, 6, 8, 10.
- `map(lambda x: x ** 2, ...)` — bình phương từng số: 4, 16, 36, 64, 100.
- Thứ tự: filter trước, map sau — đúng yêu cầu đề.

### Ví dụ chạy thử (input → output)
```
map_filter_even_squares()  →  [4, 16, 36, 64, 100]
```

### Lưu ý / mở rộng
- List comprehension một dòng: `[x**2 for x in numbers if x % 2 == 0]`.
- Lồng filter/map khó đọc hơn comprehension khi logic phức tạp.

---

## Câu 48 - Level 2

### Đề bài (tóm tắt tiếng Việt)
Dùng `filter()` tạo list các số chẵn từ 1 đến 20 (bao gồm cả hai đầu).

### Phân tích ý tưởng
- `range(1, 21)` tạo dãy 1–20.
- `filter` với điều kiện chẵn.
- Độ phức tạp: **O(n)**.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def filter_evens_1_to_20():
    """Lọc số chẵn từ 1 đến 20 bằng filter()."""
    even_numbers = list(filter(lambda x: x % 2 == 0, range(1, 21)))
    print(even_numbers)


if __name__ == "__main__":
    filter_evens_1_to_20()
```

### Giải thích code từng phần
- `range(1, 21)` — nguồn dữ liệu từ 1 đến 20.
- `lambda x: x % 2 == 0` — điều kiện số chẵn.
- Kết quả: 10 số chẵn.

### Ví dụ chạy thử (input → output)
```
filter_evens_1_to_20()  →  [2, 4, 6, 8, 10, 12, 14, 16, 18, 20]
```

### Lưu ý / mở rộng
- Cách khác: `list(range(2, 21, 2))` — bước nhảy 2, không cần filter.
- Bài này tập trung học `filter`, không tối ưu tốc độ.

---

## Câu 49 - Level 2

### Đề bài (tóm tắt tiếng Việt)
Dùng `map()` tạo list bình phương các số từ 1 đến 20 (bao gồm cả hai đầu).

### Phân tích ý tưởng
- `map` áp dụng `x ** 2` lên `range(1, 21)`.
- Độ phức tạp: **O(n)**.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
def map_squares_1_to_20():
    """Bình phương số 1-20 bằng map() và lambda."""
    squared = list(map(lambda x: x ** 2, range(1, 21)))
    print(squared)


if __name__ == "__main__":
    map_squares_1_to_20()
```

### Giải thích code từng phần
- `range(1, 21)` — 20 số nguyên.
- `map(lambda x: x ** 2, ...)` — bình phương từng số.
- `list(...)` — chuyển map object thành list hiển thị được.

### Ví dụ chạy thử (input → output)
```
map_squares_1_to_20()  →  [1, 4, 9, 16, ..., 400]
```

### Lưu ý / mở rộng
- Tương đương Câu 37 nhưng dùng `map` thay list comprehension.
- Python 3.12+: có thể dùng `[x**2 for x in range(1, 21)]` — thường được ưa chuộng hơn.

---

## Câu 50 - Level 1

### Đề bài (tóm tắt tiếng Việt)
Định nghĩa class `American` có **static method** tên `printNationality` in ra quốc tịch.

### Phân tích ý tưởng
- Static method thuộc class, không cần instance (`self`).
- Dùng decorator `@staticmethod`.
- Gọi được qua instance hoặc trực tiếp qua class: `American.printNationality()`.
- Độ phức tạp: **O(1)**.

### Code Python (chuẩn, sạch, có comment ngắn gọn)

```python
class American:
    """Class mô phỏng công dân Mỹ."""

    @staticmethod
    def printNationality():
        """In quốc tịch — không cần tham số instance."""
        print("America")


if __name__ == "__main__":
    # Gọi qua instance
    person = American()
    person.printNationality()

    # Gọi trực tiếp qua class (cách thường dùng cho static method)
    American.printNationality()
```

### Giải thích code từng phần
- `class American:` — khai báo class (Python 3 không bắt buộc kế thừa `object`).
- `@staticmethod` — đánh dấu method không nhận `self` hay `cls`.
- `printNationality()` — in chuỗi `"America"`.
- Có thể gọi `American.printNationality()` mà không cần tạo object.

### Ví dụ chạy thử (input → output)
```
person = American()
person.printNationality()  →  America
American.printNationality()  →  America
```

### Lưu ý / mở rộng
- **Static method** vs **class method** (`@classmethod`): class method nhận `cls` làm tham số đầu tiên.
- **Instance method** nhận `self` — dùng khi cần truy cập thuộc tính của object.
- Static method phù hợp cho hàm tiện ích gắn với class về mặt logic nhưng không dùng dữ liệu instance.

---

*Tổng cộng: 25 câu (Câu 26 – Câu 50)*



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



---


