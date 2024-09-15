using System;
using System.Collections.Generic;
using System.Linq;

public class Student
{
    public int Id { get; set; }
    public string Name { get; set; }
    public int Age { get; set; }
}

public class Program
{
    public static void Main()
    {
        // Khởi tạo danh sách học sinh
        List<Student> students = new List<Student>
        {
            new Student { Id = 1, Name = "Khai", Age = 20 },
            new Student { Id = 2, Name = "Vy", Age = 21 },
            new Student { Id = 3, Name = "Khoa", Age = 18 },
            new Student { Id = 4, Name = "Anh", Age = 17 },
            new Student { Id = 5, Name = "Minh", Age = 15 }
        };

        // a. In toàn bộ danh sách học sinh
        Console.WriteLine("Danh sach toan bo hoc sinh:");
        students.ForEach(student => Console.WriteLine($"Id: {student.Id}, Name: {student.Name}, Age: {student.Age}"));
        Console.WriteLine();

        // b. Tìm và in ra danh sách các học sinh có tuổi từ 15 đến 18
        var studentsAge15To18 = students.FindAll(s => s.Age >= 15 && s.Age <= 18);
        Console.WriteLine("Danh sach hoc sinh co tuoi tu 15 den 18:");
        studentsAge15To18.ForEach(student => Console.WriteLine($"Id: {student.Id}, Name: {student.Name}, Age: {student.Age}"));
        Console.WriteLine();

        // c. Tìm và in ra học sinh có tên bắt đầu bằng chữ "A"
        var studentsNameStartingWithA = students.FindAll(s => s.Name.StartsWith("A"));
        Console.WriteLine("Danh sach hoc sinh co ten bat dau bang 'A':");
        studentsNameStartingWithA.ForEach(student => Console.WriteLine($"Id: {student.Id}, Name: {student.Name}, Age: {student.Age}"));
        Console.WriteLine();

        // d. Tính tổng tuổi của tất cả học sinh
        var totalAge = students.Sum(s => s.Age);
        Console.WriteLine($"Tong tuoi cua tat ca hoc sinh: {totalAge}");
        Console.WriteLine();

        // e. Tìm và in ra học sinh có tuổi lớn nhất
        var oldestStudent = students.Aggregate((s1, s2) => s1.Age > s2.Age ? s1 : s2);
        Console.WriteLine("Hoc sinh co tuoi lon nhat:");
        Console.WriteLine($"Id: {oldestStudent.Id}, Name: {oldestStudent.Name}, Age: {oldestStudent.Age}");
        Console.WriteLine();

        // f. Sắp xếp danh sách học sinh theo tuổi tăng dần và in ra danh sách sau khi sắp xếp
        students.Sort((s1, s2) => s1.Age.CompareTo(s2.Age));
        Console.WriteLine("Sap xep danh sach hoc sinh theo tuoi tang dan:");
        students.ForEach(student => Console.WriteLine($"Id: {student.Id}, Name: {student.Name}, Age: {student.Age}"));
    }
}
