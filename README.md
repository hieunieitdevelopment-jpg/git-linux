# 🗺️ Roadmap học thuật toán & LeetCode

> Từ ZERO đến sẵn sàng phỏng vấn — Dùng JavaScript

---

## Tổng quan lộ trình

```
Giai đoạn 1 ──→ Giai đoạn 2 ──→ Giai đoạn 3 ──→ Giai đoạn 4 ──→ Giai đoạn 5 ──→ Giai đoạn 6
Nền tảng JS     Cấu trúc        Thuật toán      Pattern         Nâng cao        Thực chiến
(1-2 tuần)      dữ liệu         cơ bản          giải bài        (4 tuần)        (liên tục)
                (2-3 tuần)       (2-3 tuần)      (4-6 tuần)
```

---

## Giai đoạn 1: Nền tảng JavaScript (1-2 tuần)

> 🎯 Mục tiêu: Nắm vững cú pháp JS để không bị "kẹt" khi code thuật toán

### 1.1 Biến & Kiểu dữ liệu

```javascript
// Khai báo biến
let count = 0;        // có thể thay đổi
const MAX = 100;      // không thay đổi

// Kiểu dữ liệu cơ bản
typeof 42;            // "number"
typeof "hello";       // "string"
typeof true;          // "boolean"
typeof undefined;     // "undefined"
typeof null;          // "object" (quirk của JS)
```

### 1.2 Toán tử

```javascript
// Toán học
+  -  *  /           // cộng trừ nhân chia
%                     // chia lấy dư: 7 % 3 = 1
**                    // lũy thừa: 2 ** 3 = 8
Math.floor(3.7)       // làm tròn xuống: 3
Math.ceil(3.2)        // làm tròn lên: 4
Math.max(1, 5, 3)     // giá trị lớn nhất: 5
Math.min(1, 5, 3)     // giá trị nhỏ nhất: 1
Math.abs(-5)          // giá trị tuyệt đối: 5
Infinity              // vô cực (dùng làm giá trị khởi tạo min/max)

// So sánh
===  !==              // bằng / không bằng (LUÔN dùng 3 dấu =)
>  <  >=  <=          // lớn hơn, nhỏ hơn

// Logic
&&                    // AND: cả hai đều đúng
||                    // OR: ít nhất 1 đúng
!                     // NOT: đảo ngược
```

### 1.3 Điều kiện

```javascript
if (x > 0) {
    // x dương
} else if (x < 0) {
    // x âm
} else {
    // x = 0
}

// Ternary (viết gọn)
const result = x > 0 ? "dương" : "không dương";
```

### 1.4 Vòng lặp

```javascript
// For — dùng nhiều nhất trong thuật toán
for (let i = 0; i < n; i++) { }          // xuôi: 0 → n-1
for (let i = n - 1; i >= 0; i--) { }     // ngược: n-1 → 0
for (let i = 0; i < n; i += 2) { }       // nhảy 2 bước

// While
while (điều_kiện) { }                     // lặp khi còn đúng

// For...of — duyệt phần tử
for (const num of nums) { }              // lấy giá trị

// For...in — duyệt key (ít dùng cho thuật toán)
for (const key in obj) { }
```

### 1.5 Hàm

```javascript
// Cách 1: function declaration
function add(a, b) {
    return a + b;
}

// Cách 2: arrow function
const add = (a, b) => a + b;

// Cách 3: arrow function nhiều dòng
const add = (a, b) => {
    const sum = a + b;
    return sum;
};
```

### ✅ Checklist Giai đoạn 1
- [ ] Biết dùng `let`, `const`
- [ ] Hiểu các toán tử `%`, `Math.floor()`, `Math.max()`
- [ ] Viết được `if/else`, `for`, `while`
- [ ] Viết và gọi được function
- [ ] Hiểu `return` dừng hàm ngay lập tức

---

## Giai đoạn 2: Cấu trúc dữ liệu (2-3 tuần)

> 🎯 Mục tiêu: Biết dùng cấu trúc dữ liệu phù hợp cho từng bài toán

### 2.1 Array (Mảng) ⭐⭐⭐

```javascript
const arr = [1, 2, 3, 4, 5];

// TRUY CẬP
arr[0]              // 1 (phần tử đầu)
arr[arr.length - 1] // 5 (phần tử cuối)
arr.length          // 5

// THÊM / XÓA
arr.push(6)         // thêm cuối → [1,2,3,4,5,6]
arr.pop()           // xóa cuối → [1,2,3,4,5]
arr.unshift(0)      // thêm đầu → [0,1,2,3,4,5]
arr.shift()         // xóa đầu → [1,2,3,4,5]

// CẮT / NỐI
arr.slice(1, 3)     // cắt → [2, 3] (không đổi arr gốc)
arr.splice(1, 2)    // xóa 2 phần tử từ index 1 (ĐỔI arr gốc)
arr.concat([6, 7])  // nối → [1,2,3,4,5,6,7]

// TÌM KIẾM
arr.includes(3)     // true — có chứa 3?
arr.indexOf(3)      // 2 — vị trí của 3
arr.find(x => x > 3)       // 4 — tìm phần tử đầu tiên > 3
arr.findIndex(x => x > 3)  // 3 — tìm index đầu tiên > 3

// BIẾN ĐỔI
arr.map(x => x * 2)        // [2,4,6,8,10] — biến đổi từng phần tử
arr.filter(x => x > 3)     // [4, 5] — lọc phần tử
arr.reduce((sum, x) => sum + x, 0)  // 15 — gộp lại
arr.sort((a, b) => a - b)  // sắp xếp tăng dần
arr.reverse()               // đảo ngược

// TẠO MẢNG
new Array(5).fill(0)        // [0, 0, 0, 0, 0]
Array.from({length: 5}, (_, i) => i)  // [0, 1, 2, 3, 4]
```

**Dùng khi nào:** Hầu hết mọi bài! Mảng là cấu trúc phổ biến nhất.

### 2.2 String (Chuỗi) ⭐⭐⭐

```javascript
const str = "hello world";

str.length              // 11
str[0]                  // "h"
str.charAt(0)           // "h"

str.split("")           // ["h","e","l","l","o"," ","w","o","r","l","d"]
str.split(" ")          // ["hello", "world"]

str.includes("hello")   // true
str.indexOf("world")    // 6
str.startsWith("hello") // true

str.slice(0, 5)         // "hello"
str.toUpperCase()       // "HELLO WORLD"
str.toLowerCase()       // "hello world"
str.trim()              // xóa khoảng trắng đầu cuối

str.replace("hello", "hi")  // "hi world"

// String → Array → String (pattern rất phổ biến)
str.split("").reverse().join("")  // "dlrow olleh"

// Mã ASCII
"a".charCodeAt(0)       // 97
String.fromCharCode(97) // "a"
```

**Dùng khi nào:** Bài xử lý chuỗi, palindrome, anagram...

### 2.3 Map (Bảng băm) ⭐⭐⭐

```javascript
const map = new Map();

map.set("key", "value")   // lưu
map.get("key")             // "value" — lấy
map.has("key")             // true — kiểm tra
map.delete("key")          // xóa
map.size                   // số lượng cặp key-value
map.clear()                // xóa hết

// Duyệt Map
for (const [key, value] of map) {
    console.log(key, value);
}
```

**Dùng khi nào:** Đếm tần suất, tra cứu nhanh, Two Sum, Anagram...

### 2.4 Set (Tập hợp) ⭐⭐

```javascript
const set = new Set();

set.add(1)          // thêm
set.add(2)
set.add(1)          // KHÔNG thêm trùng → {1, 2}
set.has(1)          // true — kiểm tra
set.delete(1)       // xóa
set.size             // 1

// Xóa phần tử trùng trong mảng
const unique = [...new Set([1, 2, 2, 3, 3])]; // [1, 2, 3]
```

**Dùng khi nào:** Kiểm tra phần tử trùng, tìm unique...

### 2.5 Stack (Ngăn xếp) ⭐⭐

```javascript
// JS không có Stack riêng → dùng Array
const stack = [];

stack.push(1)     // thêm vào đỉnh
stack.push(2)
stack.push(3)     // stack = [1, 2, 3] ← đỉnh

stack.pop()       // lấy ra từ đỉnh → 3
stack[stack.length - 1]  // xem đỉnh mà không xóa → 2
stack.length === 0       // kiểm tra rỗng
```

**Nguyên tắc: LIFO** — Last In, First Out (Vào sau Ra trước)

**Dùng khi nào:** Valid Parentheses, đảo ngược, DFS...

### 2.6 Queue (Hàng đợi) ⭐⭐

```javascript
// Dùng Array (đơn giản, nhưng shift() chậm O(n))
const queue = [];

queue.push(1)      // thêm vào cuối
queue.push(2)
queue.shift()      // lấy từ đầu → 1
```

**Nguyên tắc: FIFO** — First In, First Out (Vào trước Ra trước)

**Dùng khi nào:** BFS, xử lý theo thứ tự...

### 2.7 Linked List (Danh sách liên kết) ⭐

```javascript
// Cấu trúc Node
class ListNode {
    constructor(val) {
        this.val = val;
        this.next = null;  // trỏ đến node tiếp theo
    }
}

// Tạo: 1 → 2 → 3
const head = new ListNode(1);
head.next = new ListNode(2);
head.next.next = new ListNode(3);

// Duyệt
let current = head;
while (current !== null) {
    console.log(current.val);
    current = current.next;
}
```

### 2.8 Object dùng như HashMap ⭐

```javascript
const obj = {};

obj["key"] = "value"     // lưu
obj["key"]               // "value" — lấy
"key" in obj             // true — kiểm tra
delete obj["key"]        // xóa
Object.keys(obj)         // lấy tất cả key
Object.values(obj)       // lấy tất cả value
```

### ✅ Checklist Giai đoạn 2
- [ ] Array: push, pop, slice, sort, map, filter, reduce
- [ ] String: split, join, indexOf, slice, charCodeAt
- [ ] Map: set, get, has, delete, duyệt
- [ ] Set: add, has, delete, loại trùng
- [ ] Stack: push, pop (LIFO)
- [ ] Queue: push, shift (FIFO)
- [ ] Linked List: tạo node, duyệt, thêm/xóa

---

## Giai đoạn 3: Thuật toán cơ bản (2-3 tuần)

> 🎯 Mục tiêu: Hiểu các kỹ thuật giải bài phổ biến nhất

### 3.1 Duyệt & Đếm

```javascript
// Đếm tần suất xuất hiện
function countFrequency(arr) {
    const freq = new Map();
    for (const num of arr) {
        freq.set(num, (freq.get(num) || 0) + 1);
    }
    return freq;
}
// [1,2,2,3,3,3] → Map { 1→1, 2→2, 3→3 }
```

📝 **Bài tập:** #136 Single Number, #169 Majority Element

### 3.2 Two Pointers (Hai con trỏ)

```javascript
// Kiểm tra Palindrome
function isPalindrome(s) {
    let left = 0, right = s.length - 1;
    while (left < right) {
        if (s[left] !== s[right]) return false;
        left++;
        right--;
    }
    return true;
}
// "racecar" → left đi vào, right đi ra → so từng cặp
```

📝 **Bài tập:** #125 Valid Palindrome, #167 Two Sum II, #283 Move Zeroes

### 3.3 Sliding Window (Cửa sổ trượt)

```javascript
// Tìm tổng lớn nhất của k phần tử liên tiếp
function maxSumSubarray(nums, k) {
    let windowSum = 0;

    // Tính tổng cửa sổ đầu tiên
    for (let i = 0; i < k; i++) {
        windowSum += nums[i];
    }

    let maxSum = windowSum;

    // Trượt cửa sổ: thêm bên phải, bỏ bên trái
    for (let i = k; i < nums.length; i++) {
        windowSum += nums[i] - nums[i - k];
        maxSum = Math.max(maxSum, windowSum);
    }
    return maxSum;
}
```

📝 **Bài tập:** #643 Maximum Average Subarray, #3 Longest Substring Without Repeating

### 3.4 Binary Search (Tìm kiếm nhị phân)

```javascript
// Tìm vị trí target trong mảng ĐÃ SẮP XẾP
function binarySearch(nums, target) {
    let left = 0, right = nums.length - 1;

    while (left <= right) {
        const mid = Math.floor((left + right) / 2);

        if (nums[mid] === target) return mid;       // tìm thấy
        else if (nums[mid] < target) left = mid + 1; // tìm bên phải
        else right = mid - 1;                         // tìm bên trái
    }
    return -1; // không tìm thấy
}
```

📝 **Bài tập:** #704 Binary Search, #35 Search Insert Position

### 3.5 Sorting (Sắp xếp)

```javascript
// Sắp xếp trong JS
nums.sort((a, b) => a - b);  // tăng dần
nums.sort((a, b) => b - a);  // giảm dần

// ⚠️ KHÔNG dùng nums.sort() (sắp theo string, không đúng cho số)
[10, 2, 30].sort()            // [10, 2, 30] ❌ sai!
[10, 2, 30].sort((a,b) => a-b) // [2, 10, 30] ✅ đúng!
```

📝 **Bài tập:** #242 Valid Anagram, #56 Merge Intervals

### 3.6 Recursion (Đệ quy)

```javascript
// Tính giai thừa: 5! = 5 × 4 × 3 × 2 × 1
function factorial(n) {
    if (n <= 1) return 1;       // base case — điểm dừng
    return n * factorial(n - 1); // recursive case — gọi lại chính nó
}
// factorial(5) → 5 * factorial(4) → 5 * 4 * factorial(3) → ... → 120
```

**2 phần bắt buộc:**
1. **Base case** — điều kiện dừng (KHÔNG CÓ = loop vô hạn!)
2. **Recursive case** — gọi lại chính nó với input nhỏ hơn

📝 **Bài tập:** #206 Reverse Linked List, #21 Merge Two Sorted Lists

### ✅ Checklist Giai đoạn 3
- [ ] Đếm tần suất bằng Map
- [ ] Two Pointers khi mảng sorted hoặc kiểm tra cặp
- [ ] Sliding Window cho bài "subarray liên tiếp"
- [ ] Binary Search cho mảng đã sắp xếp
- [ ] Sort đúng cách với comparator
- [ ] Đệ quy: base case + recursive case

---

## Giai đoạn 4: Pattern giải bài (4-6 tuần)

> 🎯 Mục tiêu: Nhận dạng được bài thuộc pattern nào → áp công thức

### Bảng nhận dạng Pattern

| Khi đề bài nói... | Nghĩ đến Pattern | Ví dụ bài |
|---|---|---|
| "Tìm 2 số có tổng = target" | **HashMap** | Two Sum |
| "Mảng đã sắp xếp" | **Two Pointers / Binary Search** | Two Sum II |
| "Substring/Subarray liên tiếp" | **Sliding Window** | Max Subarray |
| "Tất cả tổ hợp / hoán vị" | **Backtracking** | Permutations |
| "Đường đi ngắn nhất" | **BFS** | Shortest Path |
| "Duyệt cây / đồ thị" | **DFS / BFS** | Tree Traversal |
| "Bài toán tối ưu, chọn/không chọn" | **Dynamic Programming** | Knapsack |
| "Top K / lớn nhất / nhỏ nhất" | **Heap / Sort** | Top K Frequent |
| "Ngoặc hợp lệ / undo" | **Stack** | Valid Parentheses |
| "Merge / sắp xếp" | **Divide & Conquer** | Merge Sort |

### 4.1 Backtracking (Quay lui)

```javascript
// Tìm tất cả hoán vị
function permute(nums) {
    const result = [];

    function backtrack(current, remaining) {
        if (remaining.length === 0) {
            result.push([...current]);
            return;
        }
        for (let i = 0; i < remaining.length; i++) {
            current.push(remaining[i]);
            backtrack(current, [...remaining.slice(0, i), ...remaining.slice(i + 1)]);
            current.pop(); // ← quay lui
        }
    }

    backtrack([], nums);
    return result;
}
```

📝 **Bài tập:** #46 Permutations, #78 Subsets, #39 Combination Sum

### 4.2 DFS & BFS cho Tree

```javascript
// DFS — dùng recursion hoặc stack
function dfs(node) {
    if (!node) return;
    console.log(node.val);  // xử lý node
    dfs(node.left);          // đi trái
    dfs(node.right);         // đi phải
}

// BFS — dùng queue
function bfs(root) {
    const queue = [root];
    while (queue.length > 0) {
        const node = queue.shift();
        console.log(node.val);
        if (node.left) queue.push(node.left);
        if (node.right) queue.push(node.right);
    }
}
```

📝 **Bài tập:** #104 Max Depth of Tree, #226 Invert Tree, #102 Level Order

### 4.3 Dynamic Programming (Quy hoạch động)

```javascript
// Fibonacci — DP bottom-up
function fib(n) {
    const dp = [0, 1];
    for (let i = 2; i <= n; i++) {
        dp[i] = dp[i - 1] + dp[i - 2];
    }
    return dp[n];
}

// Climbing Stairs — có bao nhiêu cách leo n bậc (1 hoặc 2 bước)?
function climbStairs(n) {
    const dp = new Array(n + 1);
    dp[0] = 1;
    dp[1] = 1;
    for (let i = 2; i <= n; i++) {
        dp[i] = dp[i - 1] + dp[i - 2]; // từ bậc i-1 bước 1, hoặc i-2 bước 2
    }
    return dp[n];
}
```

📝 **Bài tập:** #70 Climbing Stairs, #198 House Robber, #322 Coin Change

### ✅ Checklist Giai đoạn 4
- [ ] Nhận dạng được pattern từ đề bài
- [ ] Backtracking: template chọn → đệ quy → bỏ chọn
- [ ] DFS/BFS cho tree và graph
- [ ] DP: tìm công thức truy hồi, xây bảng bottom-up

---

## Giai đoạn 5: Nâng cao (4 tuần)

> 🎯 Dành cho phỏng vấn công ty lớn

### Chủ đề cần học thêm

| Chủ đề | Độ khó | Bài tiêu biểu |
|--------|--------|----------------|
| Heap / Priority Queue | ⭐⭐⭐ | #215 Kth Largest, #347 Top K |
| Graph (DFS/BFS) | ⭐⭐⭐ | #200 Number of Islands |
| Trie | ⭐⭐⭐⭐ | #208 Implement Trie |
| Union Find | ⭐⭐⭐⭐ | #547 Number of Provinces |
| DP nâng cao | ⭐⭐⭐⭐⭐ | #300 LIS, #1143 LCS |
| Bit Manipulation | ⭐⭐⭐ | #191 Number of 1 Bits |
| Monotonic Stack | ⭐⭐⭐⭐ | #739 Daily Temperatures |

---

## Giai đoạn 6: Thực chiến — Kế hoạch luyện tập

### 📅 Lịch luyện đề gợi ý

```
Tuần 1-2:  Array + HashMap (Easy)
           #1, #217, #242, #349, #136

Tuần 3-4:  Two Pointers + String (Easy)
           #125, #283, #344, #167, #28

Tuần 5-6:  Stack + Linked List (Easy)
           #20, #206, #21, #234, #141

Tuần 7-8:  Binary Search + Sorting (Easy → Medium)
           #704, #35, #278, #56, #75

Tuần 9-10: Tree (Easy → Medium)
           #104, #226, #100, #572, #102

Tuần 11-12: Sliding Window + DP (Medium)
           #3, #121, #53, #70, #198

Tuần 13+:  Tổng hợp Medium + Hard
           #15, #322, #200, #46, #739
```

### 🔁 Quy trình giải mỗi bài

```
1. Đọc đề → hiểu INPUT / OUTPUT (5 phút)
2. Nghĩ brute force trước (5 phút)
3. Tìm pattern → tối ưu (10 phút)
4. Code ra (15 phút)
5. Test edge cases (5 phút)
6. Nếu kẹt > 30 phút → xem solution, hiểu rồi CODE LẠI
7. Comment giải thích từng bước (như bạn đã làm với Two Sum!)
```

### 📏 Đo lường tiến độ

| Cấp độ | Mục tiêu | Dấu hiệu đạt được |
|--------|----------|---------------------|
| **Beginner** | Giải Easy < 30 phút | Giải được 30+ bài Easy |
| **Intermediate** | Giải Medium < 45 phút | Giải được 20+ bài Medium |
| **Advanced** | Giải Medium < 30 phút | Nhận dạng pattern trong 5 phút |
| **Interview Ready** | Giải Medium + giải thích | Giải + nói Big O + edge cases |

---

## 📌 Tổng kết: Thứ tự ưu tiên học

```
          QUAN TRỌNG NHẤT
               ↓
    ┌──────────────────────┐
    │  1. Array + For loop │  ← bạn đang ở đây!
    │  2. Map / Set        │
    │  3. Two Pointers     │
    │  4. String xử lý     │
    │  5. Stack / Queue    │
    │  6. Sorting          │
    │  7. Binary Search    │
    │  8. Recursion        │
    │  9. Tree DFS/BFS     │
    │ 10. Dynamic Prog.    │
    │ 11. Backtracking     │
    │ 12. Graph            │
    └──────────────────────┘
               ↓
         NÂNG CAO NHẤT
```

> 💡 **Lời khuyên:** Không cần học hết rồi mới làm bài. Học đến đâu → làm bài đến đó. Mỗi ngày 1 bài, kiên trì 3 tháng sẽ thấy tiến bộ rõ rệt! 🚀
