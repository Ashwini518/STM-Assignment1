# STM-Assignment1
Assignment 1-Software Testing Methodologies

Console Application
-----------------------
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Assignment1
{
    class Program

    {
        public static int ValidateSelection()
        {
            string givenInput = "";
            bool validMenu = false;

            while (validMenu == false)
            {
                Console.WriteLine("1 = Get Rectangle Length");
                Console.WriteLine("2 = Change Length of Rectangle");
                Console.WriteLine("3 = Get Rectangle Width");
                Console.WriteLine("4 = Change Width of Rectangle");
                Console.WriteLine("5 = Get Rectangle Perimeter");
                Console.WriteLine("6 = Get Rectangle Area");
                Console.WriteLine("7 = Exit\n");

                Console.WriteLine("Please select an option, by entering a number:\n");
                givenInput = Console.ReadLine();

                if (givenInput != "1" &&
                    givenInput != "2" &&
                    givenInput != "3" &&
                    givenInput != "4" &&
                    givenInput != "5" &&
                    givenInput != "6" &&
                    givenInput != "7")
                {
                    Console.WriteLine("That's not a valid menu option, please try again:\n");
                }
                else
                {
                    validMenu = true;
                }
            }

            Console.WriteLine();
            return int.Parse(givenInput);
        }

        public static int ValidateInput(string Numbergiven)
        {
            int num = 1;
            bool isValid = false;

            while (isValid == false)
            {
                Console.WriteLine($"Please enter the {Numbergiven}:");
                string givenInput = Console.ReadLine();
                Console.WriteLine();

                bool result = int.TryParse(givenInput, out num);

                if (result == false)
                {
                    Console.WriteLine("That's not a valid input please, please try again.\n");
                }

                else
                {
                    isValid = true;
                    Console.WriteLine($"Given number is : {num}.\n");
                   
                }
            }

            return num;
        }


        static void Main(string[] args)
        {
            Rectangleclass c = new Rectangleclass();
            bool validRectangleSelect = false;
            string RectangleSelection;
            int input;

            while (validRectangleSelect == false)
            {
                Console.WriteLine("1 = Create default Rectangle of (1 unit x 1 unit)\n");
                Console.WriteLine("2 = Choose your custom numbers\n");
                Console.WriteLine("Choose a menu item to begin:");
                RectangleSelection = Console.ReadLine();
                Console.WriteLine();

                if (RectangleSelection != "1" && RectangleSelection != "2")
                {
                    Console.WriteLine("That's not a valid selection, please try again.\n");
                }
                else if (int.Parse(RectangleSelection) == 1)
                {
                    validRectangleSelect = true;  
                    int length=1;
                    int width=1;
                    Console.WriteLine($"Your default rectangle is {length} x {width}\n");
                }
                else if (int.Parse(RectangleSelection) == 2)
                {
                    validRectangleSelect = true;
                    int length;
                    int width;
                    length = ValidateInput("length");
                    width = ValidateInput("width");

                    Console.WriteLine($"Your custom Rectangle is {length} and {width}.\n");
                    Rectangleclass customRectangle = new Rectangleclass(length, width);
                    c = customRectangle;
                }
            }


            input = ValidateSelection();
            while (input != 7)
            {
                int result;
                switch (input)
                {
                    case 1:
                        Console.WriteLine($"Length is: {c.GetLength()}\n");
                        break;
                    case 2:
                        result = ValidateInput("length");
                        c.SetLength(result);
                        break;
                    case 3:
                        Console.WriteLine($"Width  is: {c.GetWidth()}\n");
                        break;
                    case 4:
                        result = ValidateInput("width");
                        c.SetWidth(result);
                        break;
                    case 5:
                        Console.WriteLine($"Perimeter of Rectangle is: {c.GetPerimeter()}\n");
                        break;
                    case 6:
                        Console.WriteLine($"Area of Rectangle is: {c.GetArea()}\n");
                        break;

                    default:
                        break;
                }
                  input = ValidateSelection();

            }

        }
    }
}
