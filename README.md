# Varargs trong Java 
## 1. Varargs trong Java là gì?
- Varargs còn được gọi là đối số biến , nó có thể truyền vào phương thức rất là nhiều đối số .  Đối số có thể chấp nhận số lượng giá trị thay đổi này được gọi là varargs.
## 2. Cách sử dụng Varargs
- Giả sử , ta có hai phương thức tính tổng như sau : 
```Java
public int tinhTong(int a,int b){
        return a+b;
    }
public int tinhTong(int a,int b,int c){
        return a+b+c;
    }
```
- Thật dễ có thể làm điều này nếu ta tính tổng với 1 , 2 chữ số . Điều gì nếu ta tính tổng 100 số ?
- Thay vào đó , ta có thể sử dụng Varargs  . Varargs có thể được coi là một Array vì nó được coi như một mảng nhưng chỉ khác là Array (mảng) không thể truyền trực tiếp tham số của mình vào phương thức hay sử dụng mảng Array chúng ta phải khởi tạo thức và truyền vào khi gọi hàm , đây không phải vấn đề quá lớn nhưng sẽ gây phiền phức hơn với quá trình code. Để sử dụng Varargs thì ta dùng ...(Ba dấu chấm) như phương thức phía dưới

```Java
    public static void main(String[] args) {
        System.out.println(tinhTong(2));
        System.out.println(tinhTong(3, 15));
    }

    public static int tinhTong(int... num) {
        int sum = 0;
        for (int x : num) {
            sum += x;
        }
        return sum;
    }
```
## 3. Lưu ý khi sử dụng Varargs  
- Varargs có thể giải quyết được vấn đề code không trong sáng , dư thừa phương thức hay vấn đề phát sinh tham số truyền vào tuy nhiên có vài lưu ý nhỏ cho những ai sử dụng Varargs :

        1. Varargs luôn phải là tham số cuối cùng
        2. Một phương thức chỉ được phép có một tham số Varargs
        3. Tránh nạp chồng phương thức (Overloading)
- Nếu không kiêng kị những điều ở trên thì việc sử dụng Varargs vào làm rõ mục đích Code trong sáng thì sai hoàn toàn . Bởi vì nếu sử dụng sai , chính bản thân phần mềm phiên dịch cũng đã không hiểu được những điều này .

## 4. Sử dụng Varargs sao cho đúng ? 
Như mình đã trình bày trong các phần trước, sử dụng varargs đúng sẽ khiến cho code trở nên trong sáng, đơn giản và đạt hiệu năng cao hơn.
- Trường hợp yêu cầu một hoặc nhiều giá trị cho tham số
  - Tham số varargs có thể nhận vào 0 hoặc nhiều giá trị. Nhưng vấn đề là có những trường hợp chúng ta mong muốn phải nhận vào ít nhật một hoặc nhiều giá trị.
```Java
public static int max(int... num) {
        int max = num[0];
        for (int i : num) {
            if (max < i) {
                max = i;
            }
        }
        return max;
    }
```
Ví dụ như trường hợp phía trên , có vấn đề gì với phương thức này ?
- Thứ nhất là ở phía người code , họ có thể hoàn toàn không truyền giá trị nào vào . Bên phía hệ thống cũng không báo lỗi và chỉ khi chạy mới biết được
- Việc code như vậy sẽ khiến code thiếu trong sáng hơn vì phương thức tập trung vào làm việc khác

Khắc phục như thế nào ?
- Chúng ta chỉ việc thêm một tham số nữa cùng với tham số dạng Varargs để phía code biết được cần truyền ít nhất một tham số .
```Java
public static int max(int index,int... num) {
        int max = index;
        for (int i : num) {
            if (max < i) {
                max = i;
            }
        }
        return max;
    }
```
## 5. Lời kết
- Không nên lạm dụng Varargs vì bản chất ,  Varargs chính là Array. Mà liên quan đến Array thì liên quan đến cấp phát bộ nhớ và hiệu năng . 
- Nhưng tất nhiên, qua bài viết phần nào anh em cũng hình dung được varargs hữu dụng trong trường hợp nào cũng như làm sao để sử dụng varargs cho đúng cách.
