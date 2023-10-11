# TryAndCatchC
50. Try Catch and Finally

Trong C#, các khối `try`, `catch` và `finally` được sử dụng để xử lý các ngoại lệ và đảm bảo rằng chương trình có thể khôi phục một cách dễ dàng từ các lỗi không mong muốn. Các khối này là một phần của cơ chế xử lý ngoại lệ của C#.

1. `try`: Khối `try` được sử dụng để đính kèm mã có thể gây ra ngoại lệ. Nếu một ngoại lệ xảy ra trong khối `try`, bộ thực thi sẽ ngay lập tức chuyển sang khối `catch` tương ứng (nếu có) để xử lý ngoại lệ.

2. `catch`: Khối `catch` theo sau khối `try` và chỉ định cách xử lý một ngoại lệ. Nó chứa mã được thực thi khi một ngoại lệ được ném vào khối `try` được liên kết. Bạn có thể bắt các loại ngoại lệ cụ thể hoặc sử dụng khối `bắt` chung để bắt tất cả các loại ngoại lệ. Việc ghi nhật ký ngoại lệ hoặc hiển thị thông báo lỗi cho người dùng trong khối `catch` là phổ biến.

3. `finally`: Khối `finally` là tùy chọn và theo sau các khối `try` và `catch`. Nó chứa mã sẽ được thực thi bất kể có ném ngoại lệ hay không. Khối `finally` thường được sử dụng để giải phóng tài nguyên như đóng tệp hoặc kết nối cơ sở dữ liệu.

Đây là một ví dụ minh họa việc sử dụng `try`, `catch` và `finally`:

```csharp
using System;

class Program
{
    static void Main()
    {
        try
        {
            // Code that might throw an exception
            int num1 = 10;
            int num2 = 0;
            int result = num1 / num2; // Division by zero will throw an exception
            Console.WriteLine("Result: " + result); // This line won't be executed
        }
        catch (DivideByZeroException ex)
        {
            // Catch the specific exception and handle it
            Console.WriteLine("Error: " + ex.Message);
        }
        catch (Exception ex)
        {
            // Catch all other exceptions (if any)
            Console.WriteLine("An error occurred: " + ex.Message);
        }
        finally
        {
            // Code in the finally block will always be executed
            Console.WriteLine("This is the finally block.");
        }

        Console.WriteLine("End of the program.");
    }
}
```
Trong ví dụ này, khối `try` chứa mã cố gắng chia hai số, nhưng `num2` được đặt thành 0, gây ra `DivideByZeroException`. Bộ thực thi nhảy tới khối `catch` phù hợp với loại ngoại lệ (`DivideByZeroException`) và hiển thị thông báo lỗi.

Khối `cuối cùng` được sử dụng để đảm bảo rằng thông báo "Đây là khối cuối cùng." được hiển thị, bất kể có ngoại lệ xảy ra hay không.

Đầu ra của chương trình này sẽ là:

```
Error: Attempted to divide by zero.
This is the finally block.
End of the program.
```
Như bạn có thể thấy, khối ` finally ` luôn được thực thi, ngay cả khi một ngoại lệ có bị bắt hay không.
1
My Code:
namespace TryAndCatchC
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Please enter a number");
            string userInput = Console.ReadLine();

            int num1 = 5;
            int num2 = 0;
            int result;

            try
            {
                result = num1 / num2;
            }
            catch (Exception)
            {

                Console.WriteLine("Can't devide by zero!");
            }

            try
            {
                int userInputAsInt = int.Parse(userInput);

            }
            catch (FormatException)
            {

                Console.WriteLine("Format exception, please enter the correct type next time.");
            }
            catch (OverflowException)
            {
                Console.WriteLine("Overflow exception, the number was too long or too short for an int32");
            }

            catch (ArgumentNullException)
            {
                Console.WriteLine("ArgumentNullException, the value was empty(null)");
            }
            finally
            {
                Console.WriteLine("This is called anyways!");
            }


            Console.ReadKey();
        }
    }
}
