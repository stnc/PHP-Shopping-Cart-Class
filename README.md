Al��veri� sepeti sistemi

Al��veri� sepeti sistemi Bu s�n�f kullan�c�lar siteyi ziyaret ederken �r�nlerin eklenebilece�i, 
"session"da saklanan bir al��veri� sepeti olu�turmam�z i�in bize yard�m eder.
Basit esnek ve kolay uygulabilir geli�mi� bir s�n�fd�r.
Al��veri� sepetindeki �r�nlerin silinmesi, miktar�n�n de�i�tirlmesi veya yeni �r�n eklenmesi gibi i�lemlere olanak sa�lar.

Sepet fonsiyonunu tan�tmak


        // e�er use olarak kullan�lacaksa
        // use \Lib\Cart;
        // $sepet = new cart($cart_name, PUBLIC_PATH);
        $cart_name = 'stnc'; // sepetin session de�erine bir de�er atad�k
        
        $cart = new \Lib\Cart('stnc', PUBLIC_PATH);

ADDTOCART fonksiyonu (Sepete �r�n ekleme)

Sepete �r�n ekleme i�in kullan�l�r ayn� id'li �r�nden tekrar eklenirse kontrol eder ve sadece �r�n�n fiyat�n� ve adetini g�nceller

http://cms.dev/sepet?action=ekle

   $cart = new \Lib\Cart('stnc', PUBLIC_PATH);
            $data = array(
                'UrunID' => 02,
                'UrunAdi' => "�ikolata  ",
                'Resim' => "biskuvi.jpg",
                'ResimURL' => "biskuvi.jpg",
                'URL' => "biskuvi.jpg",
                'Fiyat' => 40.99,
                "ToplamAdet" => 1,
                "ToplamFiyat" => ""
            );
            // sepete eklenenen her �r�n i�in benzersiz bir id verilmesi gerekir
            // 34 burada bunu temsil ediyor
            // bu mesela �u olabilir urunler tablosundaki urun_id yada sku de�eri olabilir
            // bunlar tekil de�erlerdir
            $cart->addToCart("100", $data);
            
            $data = array(
                'UrunID' => 05,
                'UrunAdi' => "kraker  ",
                'Resim' => "biskuvi.jpg",
                'ResimURL' => "biskuvi.jpg",
                'URL' => "biskuvi.jpg",
                'Fiyat' => 5,
                "ToplamAdet" => 1,
                "ToplamFiyat" => ""
            );
            $cart->addToCart("125", $data);

removeCart fonksiyonu (Sepetden �r�n silmek )

Sepetden �r�n silmek

http://cms.dev/sepet?action=sil

   $cart = new \Lib\Cart('stnc', PUBLIC_PATH);
                       $data = array(
                'UrunID' => 02,
                'UrunAdi' => "�ikolata  ",
                'Resim' => "biskuvi.jpg",
                'ResimURL' => "biskuvi.jpg",
                'URL' => "biskuvi.jpg",
                'Fiyat' => 40.99,
                "ToplamAdet" => 1,
                "ToplamFiyat" => ""
            );

            $cart->addToCart("100", $data);
            $cart->viewCart();
     		$cart->removeCart(100);
            $cart->viewCart();

viewCart fonksiyonu

Sepeti array olarak verir

http://cms.dev/sepet?action=ekle

   $cart = new \Lib\Cart('stnc', PUBLIC_PATH);
            $data = array(
                'UrunID' => 02,
                'UrunAdi' => "�ikolata  ",
                'Resim' => "biskuvi.jpg",
                'ResimURL' => "biskuvi.jpg",
                'URL' => "biskuvi.jpg",
                'Fiyat' => 40.99,
                "ToplamAdet" => 1,
                "ToplamFiyat" => ""
            );
       $cart->addToCart("125", $data);
            
           //sepet blgisini ver
           $cart-> viewCart();

GetJson fonksiyonu

Sepeti json olarak geri dond�r�r ama json de�erlerinde otomatik olarak �r�nler tablo i�inde olu�turulmu� olarak d�nerler

http://cms.dev/sepet?action=ekle

   $cart = new \Lib\Cart('stnc', PUBLIC_PATH);
            $data = array(
                'UrunID' => 02,
                'UrunAdi' => "�ikolata  ",
                'Resim' => "biskuvi.jpg",
                'ResimURL' => "biskuvi.jpg",
                'URL' => "biskuvi.jpg",
                'Fiyat' => 40.99,
                "ToplamAdet" => 1,
                "ToplamFiyat" => ""
            );
       	$cart->addToCart("125", $data);
        $cart->viewCart();
        echo $cart->getJSON();
emptyCart fonksiyonu

sepeti bo�altmak i�in kullan�l�r

http://cms.dev/sepet?action=bosalt

   $cart = new \Lib\Cart('stnc', PUBLIC_PATH);
   $cart->emptyCart();
  $cart->viewCart();
viewCartTablePrice fonksiyonu

sepetteki ler hakk�nda �r�n adet ve tutar olarak bilgi verir, mini sepet dosyas� i�indir

http://cms.dev/sepet?action=mini_sepet_fiyat

   $cart = new \Lib\Cart('stnc', PUBLIC_PATH);
   $cart->viewCartTablePrice();

//sonuc 
/*
Toplam �r�n:	2 �r�n
Toplam Adet:	4 Adet
Toplam Tutar:	91,98 TL
*/
viewCartTableFull fonksiyonu

sepetteki ler hakk�nda �r�n adet ve tutar olarak full liste bilgi verir.sepetim sayfas� bunu kullan�r

http://cms.dev/sepet?action=table

   $cart = new \Lib\Cart('stnc', PUBLIC_PATH);
   
     /*  sepet sayfas� na bas�l�cak yerdir
      * sepetteki ler hakk�nda table olarak ayr�nt�l� bilgi verir
      */
  
 echo $cart->viewCartTableFull();

cartCount fonksiyonu

sepetteki �r�n toplam� hakk�nda bilgi verir sepette ka� Adet �r�n ve ka� �r�n var

http://cms.dev/sepet?action=sepet_tutari

$cart = new \Lib\Cart('stnc', PUBLIC_PATH);
print_r( $cart->cartCount());
//��kt�s�             
/*
Array
(
    [toplam_urun] => 2
    [toplam_adet] => 4
)
*/