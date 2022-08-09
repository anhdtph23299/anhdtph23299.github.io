# Varargs trong Java 
## Varargs trong Java là gì?
- Varargs còn được gọi là đối số biến , nó có thể truyền vào phương thức rất là nhiều đối số .  Đối số có thể chấp nhận số lượng giá trị thay đổi này được gọi là varargs.
## Cách sử dụng Varargs
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
- Thay vào đó , ta có thể sử dụng varargs  . Varargs có thể được coi là một Array vì nó được coi như một mảng nhưng chỉ khác là Array (mảng) không thể truyền trực tiếp tham số của mình vào phương thức . 

```Java
public static int tinhTong(int...num){
        int sum = 0;
        for (int x : num) {
            sum+=x;
        }
        return sum;
    }
    public static void main(String[] args) {
        System.out.println(tinhTong(2,15,3));
        System.out.println(tinhTong(3,15));
    }
```
1. Có thể thấy Varargs cực kì tiện lợi nhưng có vài điểm mà nên tránh khi sử dụng : 
