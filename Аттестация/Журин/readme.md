![задание](https://user-images.githubusercontent.com/67784048/157656593-4922919e-5bd6-4895-b355-86fec51d924f.png)
![задание3](https://user-images.githubusercontent.com/67784048/157656657-2ac8e90c-0360-4147-aefb-f037cd73f3cd.png)
![задание2](https://user-images.githubusercontent.com/67784048/157663317-30bce5b0-caf6-4cec-bfcc-483ae210e439.png)
![задание4](https://user-images.githubusercontent.com/67784048/157663350-ad23a173-7668-49cc-bff4-718a901136f7.png)


Библиотека: using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ClassLibrary
{

    public class vsscodde
    
    {
     
        public void add(int a, int b)
        {
            IEnumerable<int> nums = Enumerable.Range(a, b);
            Console.WriteLine("Последовательность чисел: \n");

            foreach (int i in nums)
                Console.Write(i);
            foreach (int k in nums)
                Console.Write(k);

            double average = nums.Average();
            double min = nums.Min();
            Console.WriteLine("\n\nСреднее арифметическое: " + average);
            Console.WriteLine("\n\nМеньшее арифметическое: " + min);
        }
        public static string GetStudNumber(string student, DateTime date, int group)
        {
            var FullName = student.Split(' ');
            return $"{date.ToString("yyyy")}.{group}.{FullName[0]} {FullName[1].Substring(0, 1)}.{FullName[2].Substring(0, 1)}";
        }
    }
}

Консольное приложение: 

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Reflection;
using ClassLibraryCode;

namespace ConsoleAppCode
{

    class Program
    {
    
        static void Main(string[] args)
        {
        
            Console.WriteLine(vsscodde.GetStudNumber("Иванов Иван Иванович", DateTime.Now, Convert.ToInt32("12")));
            Assembly a = Assembly.Load("ClassLibraryCode");
            Object o = a.CreateInstance("ClassLibraryCode.vsscodde"); 
            Type t = a.GetType("ClassLibraryCode.vsscodde");
            Object[] numbers = new Object[2];
            numbers[0] = 1;
            numbers[1] = 5;
            MethodInfo mi = t.GetMethod("add");
            Console.WriteLine(mi.Invoke(o, numbers));
            Console.ReadLine();
        }
    }
    
}

   
