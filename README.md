# STM-Assignment1
Assignment 1-Software Testing Methodologies

Rectangle Class
------------------
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Assignment1
{
    public class Rectangleclass
    {
        private int length;
        private int width;
        public Rectangleclass()
        {
            length = 1;
            width = 1;
        }
        public Rectangleclass(int length, int width)
        {
            this.length = length;
            this.width = width;
        }
        public int GetLength()
        {
            return length;
        }
        public int SetLength(int length)
        {
            this.length = length;
            return this.length;
        }
        public int GetWidth()
        {
            return width;
        }
        public int SetWidth(int width)
        {
            this.width = width;
            return this.width;
        }
        public int GetPerimeter()
        {
            return (length * 2) + (width * 2);
        }
        public int GetArea()
        {
            return length * width;
        }
    }
}
