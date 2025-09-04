# Đoạn mã

Mục này mô tả các đoạn mã JavaScript có thể được áp dụng trong ứng dụng.

## Debounce

### Giải thích
Debounce hợp nhất nhiều thao tác (sự kiện) xảy ra liên tiếp trong một khoảng thời gian nhất định thành một lần gọi duy nhất.  
Đây là kỹ thuật được sử dụng để kiểm soát các sự kiện được kích hoạt thường xuyên, chẳng hạn như thay đổi kích thước cửa sổ hoặc nhập phím,  
cũng như ngăn việc xử lý bị thực thi nhiều lần ngoài ý muốn do hành động của người dùng.  

Debounce mang lại những lợi ích sau:  
- **Cải thiện hiệu suất**  
  Giảm bớt các lần thực thi hàm không cần thiết, giúp cải thiện hiệu suất ứng dụng.  
- **Giảm chi phí API**  
  Giảm số lần gọi API không cần thiết, giúp tiết kiệm tài nguyên.  
- **Cải thiện trải nghiệm người dùng**  
  Ngăn chặn hành vi không mong muốn hoặc các hoạt ảnh dư thừa, đảm bảo trải nghiệm người dùng hiệu quả.  

Cụ thể, Debounce giải quyết các vấn đề sau:  
- Quá trình gửi (Submit) bị thực thi nhiều lần do người dùng thao tác lặp lại  
- API bị gọi mỗi khi nhập phím, gây lo ngại về hiệu suất  

see: [MDN - Debounce](https://developer.mozilla.org/en-US/docs/Glossary/Debounce)

### function

```javascript
    /**
    * debounce()
    * Creates and returns a new debounced version of the given function.
    * This function delays execution until after the specified wait (ms) 
    * has elapsed since the last time it was invoked.
    * Useful for implementing behavior that should only occur 
    * once input has stopped arriving.
    * If the immediate argument is set to true, the function will be triggered 
    * at the start of the wait interval instead of the end.
    * This is helpful to prevent unintended double executions, 
    * such as when a "Submit" button is accidentally clicked twice.
    * @param {Function} func Function to debounce
    * @param {Number} wait Delay interval (milliseconds)
    * @param {Boolean} immediate Immediate trigger flag
    * @returns
    */
    function debounce(func, wait, immediate) {
        let timeout;
        return function() {
                const context = this, args = arguments;
                clearTimeout(timeout);
                timeout = setTimeout(function() {
                        timeout = null;
                        if (!immediate) func.apply(context, args);
                }, wait);
                if (immediate && !timeout) func.apply(context, args);
        };
    };
```

### Ví dụ sử dụng

Đây là ví dụ về cách sử dụng Debounce cho sự kiện **liveChange** khi nhập vào trường Input.  
Truyền hàm bạn muốn áp dụng vào đối số thứ nhất của `debounce()`.  
Thiết lập thời gian trễ (tính bằng mili giây) vào đối số thứ hai của `debounce()`.  
Trong ví dụ dưới đây, ngay cả khi `onChangeInput` được gọi nhiều lần trong vòng 0,5 giây,  
nó sẽ chỉ được thực thi một lần duy nhất.  

```javaScript
    onChangeInput: debounce(function (oEvent) {
    ....
    }, 500),
```

