## EXO 01

```C#
internal class Program
{
    private static void Main(string[] args)
    {
        double[] valeurs = new double[3];

        Console.Write("Entrez la première valeur : ");
        valeurs[0] = Convert.ToDouble(Console.ReadLine());

        Console.Write("Entrez la deuxième valeur : ");
        valeurs[1] = Convert.ToDouble(Console.ReadLine());

        Console.Write("Entrez la troisième valeur : ");
        valeurs[2] = Convert.ToDouble(Console.ReadLine());

        Array.Sort(valeurs);

        Console.WriteLine($"Valeurs : {valeurs[0]}, {valeurs[1]}, {valeurs[2]}");
    }
}
```

## EXO 02

```C#
internal class Program
{
    private static void Main(string[] args)
    {
        string nom;
        double note;

        while (true)
        {
            Console.WriteLine("Saissisez un nom d'élève : ");
            nom = Console.ReadLine();
            Console.WriteLine("Saissisez sa note : ");
            note = Convert.ToDouble(Console.ReadLine());
            while (note < 0 || note > 20)
            {
                Console.WriteLine($"{nom} a une note impossible, ressaisissez la note");
                note = Convert.ToDouble(Console.ReadLine());
            }
            if (note >= 10)
            {
                Console.WriteLine($"{nom} est admis.e avec la note de {note}/20 ");
            }
            else
            {
                Console.WriteLine($"{nom} n'est pas admis.e avec la note de {note}/20 ");
            }
        }
    }
}
```

