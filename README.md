# myproqram
public
# 1. GitHub-dan repository-ni klonla
git clone https://github.com/username/myprogram.git

# 2. Layihənin içində çalış
cd myprogram

# 3. Fayllarını əlavə et
git add .

# 4. Dəyişiklikləri qeyd et
git commit -m "Ilk versiya yuklendi"

# 5. GitHub-a yüklə
git push origin main
using System;
using System.Collections.Generic;

namespace SatisProgrami
{
    class Urun
    {
        public string Ad { get; set; }
        public double Qiymet { get; set; }
        public int Say { get; set; }

        public Urun(string ad, double qiymet, int say)
        {
            Ad = ad;
            Qiymet = qiymet;
            Say = say;
        }
    }

    class Program
    {
        static List<Urun> urunler = new List<Urun>();

        static void Main(string[] args)
        {
            while (true)
            {
                Console.WriteLine("1. Yeni məhsul əlavə et");
                Console.WriteLine("2. Məhsulları göstər");
                Console.WriteLine("3. Məhsul satışı");
                Console.WriteLine("4. Çıxış");
                Console.Write("Seçiminizi edin: ");
                string secim = Console.ReadLine();

                switch (secim)
                {
                    case "1":
                        YeniUrunElaveEt();
                        break;
                    case "2":
                        MehsullariGoster();
                        break;
                    case "3":
                        MehsulSatis();
                        break;
                    case "4":
                        return;
                    default:
                        Console.WriteLine("Yanlış seçim!");
                        break;
                }
                Console.WriteLine();
            }
        }

        static void YeniUrunElaveEt()
        {
            Console.Write("Məhsul adı: ");
            string ad = Console.ReadLine();
            Console.Write("Qiymət: ");
            double qiymet = Convert.ToDouble(Console.ReadLine());
            Console.Write("Say: ");
            int say = Convert.ToInt32(Console.ReadLine());

            urunler.Add(new Urun(ad, qiymet, say));
            Console.WriteLine("Məhsul əlavə olundu!");
        }

        static void MehsullariGoster()
        {
            Console.WriteLine("Mövcud məhsullar:");
            foreach (var urun in urunler)
            {
                Console.WriteLine($"{urun.Ad} - Qiymət: {urun.Qiymet} - Say: {urun.Say}");
            }
        }

        static void MehsulSatis()
        {
            Console.Write("Satmaq istədiyiniz məhsul adı: ");
            string ad = Console.ReadLine();
            var urun = urunler.Find(u => u.Ad == ad);

            if (urun != null)
            {
                Console.Write("Satılacaq say: ");
                int say = Convert.ToInt32(Console.ReadLine());

                if (urun.Say >= say)
                {
                    urun.Say -= say;
                    Console.WriteLine($"Satış tamamlandı. Qalıq say: {urun.Say}");
                }
                else
                {
                    Console.WriteLine("Yetərli məhsul yoxdur!");
                }
            }
            else
            {
                Console.WriteLine("Məhsul tapılmadı!");
            }
        }
    }
}
