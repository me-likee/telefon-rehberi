# telefon-rehberi

using System.Collections.Generic;
using System.Collections;
namespace Name
{
    
    class telefon
        {
            static void Main(string[] args)
            {
                    kayıt kayıtlar=new kayıt();
                    Console.WriteLine("1 Ekleme");
                    Console.WriteLine("2 Silme");
                    Console.WriteLine("3 listeleme");
                    Console.WriteLine("4 Güncelleme");
                    int ops=int.Parse(Console.ReadLine());
                switch (ops)
                {
                    case 1:
                    Console.Write("İsim   : ");
                    string name = Console.ReadLine();
                    Console.Write("Numara : ");
                    long number = long.Parse(Console.ReadLine());
                    kayıtlar.recordAdd(number,name);
                    break;

                    case 2:
                    Console.Write("Numara : ");
                    long numara = long.Parse(Console.ReadLine());
                    kayıtlar.recordDel(numara);
                    break;

                    case 3:
                    Console.Write(" listeleme ");
                    kayıtlar.listeleme();
                    break;

                    case 4:
                    Console.Write("Name : ");
                    string güncelisim = Console.ReadLine();
                    kayıtlar.recordUpdate(güncelisim);
                    break;

                    
                    case 5:
                    etiket:
                    Console.Write("isime göre arama yapmak 1");
                    // Console.Write("Numaraya göre arama yapmak 2");
                    int choise = int.Parse(Console.ReadLine());
                    if (choise==1)
                    {
                        Console.WriteLine("Arancak ismi giriniz:");
                        string aranacakisim=Console.ReadLine();
                        kayıtlar.arama(aranacakisim);
                    }
                    // else if(choise==2)
                    // {
                    //     Console.WriteLine("Arancak numara giriniz:");
                    //     long arancaknumara=long.Parse(Console.ReadLine());
                    //     kayıtlar.arama(arancaknumara);
                    // } 
                    else
                    {
                        Console.WriteLine("Yanlış seçim yaptınız");
                        goto etiket;
                    }
                    break;
                }
            }
        }
    class kayıt
        {
            Dictionary<long,string> numaralar = new Dictionary<long, string>();
            public void recordAdd(long number,string name)
            {
                numaralar.Add(number, name);
                Console.WriteLine("{0} {1} Kişi Başarılı Şekilde Kaydedilmiştir.", name, number);
            }   

            public void recordDel(long numara)
            {
                numaralar.Remove(numara);
                Console.WriteLine("{0}  Kişi Başarılı Şekilde Silinmiştir.", numara);
            }

            public void listeleme()
            {
                Console.WriteLine("Name              Number");
                foreach(var item in numaralar)
                {
                    Console.WriteLine("{0}      => {1}", item.Key, item.Value);
                }
            }

             public void recordUpdate(string güncelisim)
                {
                    foreach (var item in numaralar)
                    {
                        if(item.Value.Contains(güncelisim))
                        {
                            Console.WriteLine("lütfen Değiştirmek istediğiniz numarayı giriniz:");
                            long no=long.Parse(Console.ReadLine());
                            string isim = item.Value;
                            numaralar.Remove(item.Key);
                            numaralar.Add(no,isim);

                    
                        }
                    }

                    Console.WriteLine("{0}  Kişi Başarılı Şekilde Güncellenmiştir.", güncelisim);
                }

                   public void arama(string aranacakisim)
            {
                foreach (var item in numaralar)
                {
                    if(item.Value.Contains(aranacakisim))
                    {
                        Console.WriteLine("İsim-Soyisim:" + item.Value);
                        Console.WriteLine("Telefon Numarası:" + item.Key);
                    }
                }
            }   

            
        }
    }
