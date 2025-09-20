using System;

class Program
{
    static void Main()
    {
        while (true)  // infinite loop until user exits
        {
            Console.WriteLine("Enter operation (+, -, *, /) or q to quit:");
            var op = Console.ReadLine();   
            if (op == "q") break;        

            Console.Write("A: ");
            if (!decimal.TryParse(Console.ReadLine(), out var a))
            {
                Console.WriteLine("Invalid A");
                continue;
            }

            Console.Write("B: ");
            if (!decimal.TryParse(Console.ReadLine(), out var b))
            {
                Console.WriteLine("Invalid B");
                continue;
            }

            try
            {
                decimal result = op switch
                {
                    "+" => a + b,
                    "-" => a - b,
                    "*" => a * b,
                    "/" => b == 0 ? throw new DivideByZeroException() : a / b,
                    _ => throw new InvalidOperationException("Unknown op")
                };
                Console.WriteLine($"Result: {result}");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error: {ex.Message}");
            }
        }
    }
}
