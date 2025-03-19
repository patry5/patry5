using System;

class Program
{
    static void Main()
    {
        Console.Write("Podaj tekst do zaszyfrowania: ");
        string tekst = Console.ReadLine();
        Console.Write("Podaj klucz: ");
        int klucz = int.Parse(Console.ReadLine());

        Console.WriteLine(SzyfrCezara(tekst, klucz));
    }

    static string SzyfrCezara(string tekst, int klucz)
    {
        string wynik = "";
        for (int i = 0; i < tekst.Length; i++)
        {
            char znak = tekst[i];
            if ((znak >= 'a' && znak <= 'z') || (znak >= 'A' && znak <= 'Z'))
            {
                char baza = (znak >= 'A' && znak <= 'Z') ? 'A' : 'a';
                int przesuniecie = (znak - baza + klucz) % 26;
                char nowyZnak = (char)(baza + przesuniecie);
                wynik += nowyZnak;
            }
            else
            {
                wynik += znak;
            }
        }
        return wynik;
    }
}