# SOKOBAN-C-
SOKOBAN C#
```C#
using System;

class Program
{
    static void Main(string[] args)
    {
        int x = 4, y = 4; // КООРДИНАТЫ ИГРОКА
        //- КООРДИНАТЫ СТЕН 
        int shirina = 10;
        int visota = 15; 
        //----
        char[,] maze = new char[shirina, visota]; // СТЕНЫ
        int xWall = 6, yWall = 6;
        char[,] wall = new char[xWall, yWall]; // МАССИВ ДЛЯ ХРАНЕНИЯ КООРДИНАТ ПРИПЯТСВИЙ

        int xKorobka = 4, yKorobka = 4; // КОРОБКА
        int xMesto = 8, yMesto = 3;

        while (true)
        {
            ConsoleKeyInfo keyboard = Console.ReadKey(true);
            Console.Clear();
            switch (keyboard.Key)
            {
                case ConsoleKey.W:
                    if (y > 1)
                    {
                        y -= 1;
                    }
                    if (y == yKorobka && x == xKorobka)
                    {
                        if (yKorobka > 1)
                        {
                            yKorobka -= 1;
                        }

                    }
                    break;
                case ConsoleKey.A:
                    if (x > 1)
                    {
                        x -= 1;
                    }

                    if (y == yKorobka && x == xKorobka)
                    {
                        if (xKorobka > 1)
                        {
                            xKorobka -= 1;
                        }

                    }

                    break;
                case ConsoleKey.S:
                    if (y < 8)
                    {
                        y += 1;
                    }

                    if (y == yKorobka && x == xKorobka)
                    {
                        if (yKorobka < 8)
                        {
                            yKorobka += 1;
                        }
                    }
                    break;
                case ConsoleKey.D:
                    if (x < 13)
                    {
                        x += 1;
                    }
                    if (x == xKorobka && y == yKorobka)
                    {
                        if (xKorobka < 13)
                        {
                            xKorobka += 1;
                        }

                    }
                    break;
            }
            //-----------КОЛИЗИЯ-------------
            for (int i = 0; i < shirina; i++)
            {
                maze[i, 0] = '#';
                maze[i, visota - 1] = '#';
            }
            for (int i = 6; i < 9; i++)
            {
                maze[5, i] = '$';
            }

            for (int i = 0; i < visota; i++)
            {
                maze[0, i] = '#';
                maze[shirina - 1, i] = '#';
            }

            for (int i = 0; i < shirina; i++)
            {
                for (int j = 0; j < visota; j++)
                {
                    if (maze[i, j] == '#')
                    {
                        Console.ForegroundColor = ConsoleColor.DarkYellow; 
                    }
                    else
                    {
                        Console.ResetColor();
                    }
                    Console.Write(maze[i, j]);
                }
                Console.WriteLine();
            }

            if (xKorobka == xMesto && yKorobka == yMesto)
            {
                Console.SetCursorPosition(xKorobka, yKorobka);
                Console.ForegroundColor = ConsoleColor.Yellow;
                Console.Write("@");
            }
            else
            {
                Console.SetCursorPosition(xKorobka, yKorobka);
                Console.ForegroundColor = ConsoleColor.Red;
                Console.Write("@");
            }
            Console.SetCursorPosition(xMesto, yMesto);
            Console.ForegroundColor = ConsoleColor.White;
            Console.Write("%");

            //-------------------------
            Console.SetCursorPosition(x, y);
            Console.ForegroundColor = ConsoleColor.Green;  
            Console.Write("#");

            Console.ResetColor();

            Console.ResetColor();
        }
    }
}
```
