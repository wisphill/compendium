```bash
# Golang Algo Cheat Sheet

## Khai báo & Cơ bản
- Khai báo nhanh: `x := 10`
- Mảng cố định: `arr := [5]int{1, 2, 3, 4, 5}`
- Độ dài: `len(arr)`

## Slice (Mảng động)
- Khai báo: `s := []int{}` hoặc `s := make([]int, length, capacity)`
- Thêm phần tử: `s = append(s, val)`
- Cắt slice: `sub := s[start:end]` (không gồm end)
- Copy slice: `copy(dest, src)` (phải `make` dest trước)
- Xóa phần tử tại i: `s = append(s[:i], s[i+1:]...)`

## Map (Hash Table)
- Khai báo: `m := make(map[keyType]valueType)`
- Thêm/Sửa: `m[key] = val`
- Xóa key: `delete(m, key)`
- Kiểm tra tồn tại: `val, exists := m[key]`

## Vòng lặp & Duyệt dữ liệu
- Vòng lặp for cơ bản: `for i := 0; i < n; i++ {}`
- Vòng lặp while: `for condition {}`
- Vòng lặp vô hạn: `for {}`
- Duyệt Slice: `for index, val := range s {}`
- Duyệt Map: `for key, val := range m {}`

## Điều kiện
- If cơ bản: `if condition {} else {}`
- If với khai báo nhanh: `if val, ok := m[key]; ok {}`
- Switch case: `switch x { case 1: ... default: ... }`

## Chuỗi (String / Rune / Byte)
- Chuỗi sang slice byte: `b := []byte(str)`
- Chuỗi sang slice rune (Unicode): `r := []rune(str)`
- Ký tự tại i (ASCII): `ch := str[i]` (trả về byte)
- Ghép chuỗi (hiệu năng cao): `var sb strings.Builder; sb.WriteString("a"); s := sb.String()`

## Hàm toán học (Math)
- Ép kiểu số thực để dùng toán học: `float64(x)`
- Giá trị tuyệt đối: `math.Abs(x)`
- Lớn nhất/Nhỏ nhất: `math.Max(x, y)`, `math.Min(x, y)`
- Mũ/Căn bậc hai: `math.Pow(x, y)`, `math.Sqrt(x)`
- Làm tròn: `math.Floor(x)`, `math.Ceil(x)`
- Giá trị vô cực: `math.MaxInt64`, `math.MinInt64`, `math.MaxInt32`

## Sắp xếp (Sort)
- Sắp xếp số nguyên: `sort.Ints(sliceInt)`
- Sắp xếp chuỗi: `sort.Strings(sliceString)`
- Sắp xếp tùy biến (custom): `sort.Slice(s, func(i, j int) bool { return s[i] < s[j] })`
- Tìm kiếm nhị phân (trên slice đã sort): `idx := sort.SearchInts(sliceInt, target)`

## Ngăn xếp & Hàng đợi (Stack & Queue dùng Slice)
- Stack Push: `stack = append(stack, val)`
- Stack Pop: `val := stack[len(stack)-1]; stack = stack[:len(stack)-1]`
- Queue Push: `queue = append(queue, val)`
- Queue Pop: `val := queue[0]; queue = queue[1:]`
  
## Slice nâng cao & Thủ thuật giải thuật
- Khởi tạo slice có giá trị mặc định: `s := make([]int, n); for i := range s { s[i] = defaultVal }`
- Tạo slice trọn vẹn từ mảng: `s := arr[:]` 
- Tạo slice từ chỉ số i đến j-1: `s := arr[i:j]`
- Đảo ngược slice (Reverse): `for i, j := 0, len(s)-1; i < j; i, j = i+1, j-1 { s[i], s[j] = s[j], s[i] }`
- Xóa toàn bộ phần tử (Clear giữ nguyên cap): `s = s[:0]`
- Cắt slice từ đầu đến i: `left := s[:i]`
- Cắt slice từ i đến hết: `right := s[i:]`
- Thêm toàn bộ một slice khác vào sau: `s = append(s, anotherSlice...)`
- Sắp xếp tăng dần (mọi kiểu dữ liệu primitive): `slices.Sort(s)`
- Sắp xếp giảm dần: `slices.SortFunc(s, func(a, b int) int { return cmp.Compare(b, a) })` 
- Sắp xếp struct theo trường: `slices.SortFunc(users, func(a, b User) int { return cmp.Compare(a.Age, b.Age) })`
```