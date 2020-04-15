---
published: true
title: 'Ngày 2 - Lời giải đề thi HSG quốc gia môn tin học năm 2020'
layout: post
date: '2020-04-15'
tags:
  - CS
---
Solution ngày 1: [blog](/2020-02-23-VOI2020Solution-day1)
Đề thi ngày 2: [PDF](/data/VOI2020/VOI2020_day_2.pdf)

Link nộp bài: [VOI2020](https://codeforces.com/group/FLVn1Sc504/contest/266446). Các bạn cần vào group: [Vietnamese Competitive Programmers](https://codeforces.com/group/FLVn1Sc504) trước nếu không vào được link contest.

Với các bài, nếu đề quá dài mình sẽ tóm tắt lại đại ý trước khi đi vào lời giải. Mình sẽ chủ yếu đi vào lời giải cho sub cuối cùng, nhưng sẽ nói sơ qua các cách vét điểm.

## Bài 4: LIGHT

- Tag: Greedy, 2D prefix sum

### Tóm tắt đề bài

Có một ma trận $$m \times n$$, mỗi ô mang giá trị từ 0 tới 2. Ta có $$k$$ nút bấm có dạng $$(r_i, c_i), (x_i, y_i)$$. Khi bấm một nút thì toàn bộ các ô nằm trong ma trận con của nút đó được tăng giá trị lên 1 (trong modulo 3, nghĩa là 2 thì sẽ chuyển về 0). Nhiệm vụ của bạn là tìm số lần bấm ít nhất để toàn bộ ma trận có giá trị là 1, hoặc toàn bộ có giá trị là 2. Một điều kiện **rất quan trọng** là $$(r_i, c_i)$$ khác nhau với mọi $i$. 

### Lời giải

Một số nhận xét trước khi làm bài:
1. Thứ tự bấm các nút không quan trọng.
2. Số lần bấm 1 nút không quá 2 lần.

#### Subtask 1: $$m = 1, n \leq 10$$

Subtask này nhiều cách để trâu lắm, dự trên nhận xét 2 ở trên, có thể sinh $$3^k$$ cách bấm rồi kiểm tra.

#### Subtask 2: $$m * n \leq 10^3$$

Hãy xem xét cách biến đổi toàn bộ bảng về một giá trị $$t$$. Ta sẽ cố gắng biến đổi ô $$(1, 1)$$ về $$t$$, sau đó là ô $$(1, 2), (1, 3), ..., (1, n)$$, sau đó tiếp tục tới hàng thứ 2, 3, ... 

Xét ô $$(1, 1)$$, rõ ràng duy nhất chỉ có nhiều nhất một nút bấm ảnh hưởng tới nó, vậy nếu ô $$(1, 1)$$ mà khác giá trị $$t$$, rõ ràng ta cần phải bấm (và ta biết chính xác là cần phải bấm bao nhiêu lần), còn nếu không có nút bấm thì rõ ràng không thể biến toàn bộ bảng về giá trị $$t$$. Điều này thực hiện được là nhờ điều kiện tất cả $$(r_i, c_i)$$ của mọi truy vấn là phân biệt (nếu không có điều kiện đó thì mình cũng không biết bài này làm thế nào). 

Sau khi bấm xong ở ô $$(1, 1)$$ thì ta xem như là xóa nó đi, tương tự sang ô $$(1, 2)$$ cũng chỉ có nhiều nhất 1 nút bấm ảnh hưởng tới nó. Tiếp tục quy nạp tiếp tục thì ta sẽ xét được hết bảng.

Do giới hạn nhỏ, nên mỗi lần bấm nút ta có thể thực hiện duyệt qua toàn bộ ô được ảnh hưởng bởi nút bấm đó và điều chỉnh lại giá trị.

#### Subtask 3: $$m * n \leq 10^5$$

Ở subtask này thì việc duyệt qua toàn bộ ô bị ảnh hưởng là không khả thi, và hiển nhiên là ta cần phải optimize chỗ này, ta xem xét kĩ hơn ở những việc cần làm:

1. Cập nhật toàn bộ ô trong một hình chữ nhật lên một giá trị $$t$$
2. Tính giá trị tại một ô. 

Tới đây thì nhiều bạn dùng cây [Fenwick tree 2D](https://www.geeksforgeeks.org/two-dimensional-binary-indexed-tree-or-fenwick-tree/) để thực hiện các truy vấn này, độ phức tạp là $$O(m \times n \times log(m) \times log(n))$$. 

Nhưng nếu để ý hơn thì ta nhận thấy là ở các truy vấn lấy giá trị tại một ô, các ô được lấy "tăng dần" (ta lấy ô $$(1, 1)$$ rồi tới ô $$(1, 2), (1, 3), \dots$$, do đó ta chỉ cần một mảng prefix sum 2D là đủ, và dùng thêm trick [này](https://codeforces.com/blog/entry/50185?#comment-340926). 

Độ phức tạp là $$O(m \times n)$$

Code tham khảo: [LIGHT.cpp](/data/VOI2020/LIGHT.cpp)

## Bài 5: BUILDING

- Tag: Sweep line, cạnh cầu.

### Tóm tắt đề bài:


### Lời giải:

Code tham khảo: [BUILDING.cpp](/data/VOI2020/BUILDING.cpp)

## Bài 6: EQUAKE

- Tag: DP on tree

### Lời giải:
Code tham khảo: [EQUAKE.cpp](/data/VOI2020/EQUAKE.cpp)
