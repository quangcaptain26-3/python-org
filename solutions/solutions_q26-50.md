# Lời giải chi tiết Python - Câu 26 đến 50

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
