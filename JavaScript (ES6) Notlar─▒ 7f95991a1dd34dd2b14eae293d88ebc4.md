# JavaScript (ES6) Notları

- Değişken Tanımlama
    - "var" Değişkeni
        - var ile tanımladığın değişkeni daha sonra tekrar tanımlayabilirsin.
            
            ```jsx
            var degisken = "Değişken 1"
            var degisken = "Değişken 2"
            console.log(degisken);
            //konsolda Değişken 2 çıktısını alırız.
            ```
            
        - var ile, değişkeni önce kullanıp daha sonra tanımlayabilirsin.
            
            ```jsx
            degisken="Degisken 1";
            console.log(degisken);
            var degisken;
            ```
            
        - var değişkeni içerisinde bulunduğu fonksiyon içerisinde erişilebilir.
            
            ```jsx
            // Eğer var kullanamzsak, değişken global scope olur ve fonksiyon
            // dışından da çağırılabilir.
            function hello(){
            	greeting = "Hello World";
            }
            hello();
            console.log(greeting); //konsolda Hello World yazacaktır. 
            
            //var kullandığımızda ise değişken sadece fonksiyon içinde erişilebilir.
            function hello(){
            var greeting = "Hello World";
            }
            hello();
            console.log(greeting); //greeting fonksiyon dışında tanımlı olmadığından
            // konsolda hata alırız.
            ```
            
    - "let" Değişkeni
        - let ile tanımladığın değişken sadece içinde bulunduğu bloktan erişilebilir.
            
            ```jsx
            function hello(){
            	{
            		{
            			let greeting = "Hello World";
            			console.log(greeting);
            		}
            		console.log(greeting);
            	}
            	console.log(greeting);
            }
            //bu kod çalıştırıldığında konsolda ilk olarak Hello World çıktsını alırız
            //ancak devamında greeting tanımlı olmadığı için hata alırız. Sadece ilk 
            //bloktaki console.log komutu bir değer döndürür.
            ```
            
        - let ile tanımladığın değişkeni daha sonra tekrar tanımlayamazsın ancak değerini güncelleyebilirsin.
            
            ```jsx
            let degisken = "Değişken 1";
            let degisken = "Değişken 2";
            // bu kodu çalıştırdığımızda Syntax Error alırız. Çünkü degisken
            // daha önce tanımlanmıştır.
            
            let degisken = "Değişken 1";
            degisken = "Değişken 2";
            console.log(degisken);
            // Eğer bu kodu çalıştırırsak konsolda Değişken 2 çıktısını alırız.
            ```
            
    - "const" Değişkeni
        - const ile tanımlanan değişken hiçbir koşulda tekrar tanımlanamaz veya güncellenemez.
        - const diğerlerine göre daha az mantıksal hataya sebebiyet verir. Daha basit kullanımlar içindir.
- Template Literals Kullanımı
    - Embedding
        - Backsticks kullanarak değişkenleri metnin içine yerleştirebiliriz.
            
            ```jsx
            //Değişkenleri bu şekilde metnin içine entegre edebiliriz.
            var name = "Barış";
            var surname = "Emren";
            console.log(`Merhaba benim adım ${name}, soyadım ${surname}`);
            
            //Veya başka bir örnek:
            var my = {
            	name:"Barış",
            	surname:"Emren"
            }
            console.log(`Merhaba benim adım ${my.name}, soyadım ${my.surname}`);
            
            ```
            
    - Multiline
        - Yeni satır veya Tab işlemleri için kullanabiliriz.
            
            ```jsx
            const sentence = `Merhaba      benim 
               								adım Barış`;
            console.log(sentence);		
            ```
            
- Veri Türü Öğrenme Değiştirme
    - Veri Türü Öğrenme
        - Veri türünü öğrenmek için "typeof" operatörü kullanılır.
            
            ```jsx
            let price = 11;
            let name = "Coffee";
            let inStock = true;
            console.log(typeof(price),typeof(name),typeof(inStock));
            ```
            
    - string Türünden float ve int Türüne Dönüştürme
        - string'den float'a dönüştürmek için "parseFloat" operatörü kullanılır.
            
            ```jsx
            let pixel_count = "16.7";
            pixel_count = parseFLoat(pixel_count);
             
            ```
            
        - string'den int'e dönüştürmek için "parseInt" operatörü kullanılır.
            
            ```jsx
            let pixel_count = "16";
            pixel_count = parseInt(pixel_count);
            ```
            
        - number'dan string'e dönüştürmek için "toString" operatörü kullanılır.
            
            ```jsx
            let number1 = 55;
            number1 = number1.toString();
            ```
            
- String Veri Türü İle İşlemler
    - İfadenin İçindeki Aradığımız Karakteri Bulmak.
        - Bunun için 2 yöntem vardır. chatAt() ve [ ] .
            
            ```jsx
            let lecture = "JavaScript Lessons";
            console.log(lecture.charAt(5));
            console.log(lecture[5]);
            //iki komutun çıktısı da aynıdır ve 'c' stringini döndürür.
            ```
            
    - String İçinde Arama Yapmak.
        - Arama yapmak için "search()" kullanılır.
            
            ```jsx
            let email = "user@website.com";
            console.log(email.search("@"));
            //çıktı olarak '4' alırız.
            ```
            
    - Metin İçinden İstediğimiz Bir Bölümü Almak.
        - Metin içindeki belli bir bölüm ve sonrasını almak için slice(x) kullanılır.
            
            ```jsx
            let email = "user@website.com";
            console.log(email.slice(email.search("@") + 1));
            //burada '@' karakterinden sonrası yani 'website.com' döndürülür
            ```
            
        - Metin içindeki istediğimiz bölümü almak için slice(x,y) kullanılır.
            
            ```jsx
            let email = "user@website.com";
            console.log(email.slice(0,email.search("@")));
            //burada ilk karakter ile '@' karakteri arasında kalan bölüm döndürülür
            //yani 'user' çıktısı alınır.
            ```
            
    - Metin İçindeki Bir Bölümü Değiştirmek
        - Bunun için replace('a','b') operatörü kullanılır.
            
            ```jsx
            let email = "user@website.com";
            email = email.replace('website.com','hotmail.com');
            // bununla birlikte yeni email 'user@hotmail.com' olur.
            ```
            
- DOM İle Çalışmak
    - Dom İçerisinden Veri Çekmek
        - Veri çekmek için kullanılan yollardan biri getElementsById() operatörüdür.
            
            ```jsx
            let title = document.getElementById("title");
            title.innerHTML = "Başlık Değişti.";
            ```
            
        - Diğer yol ise querySelector() operatörüdür.
            
            ```jsx
            // ID ile arama yapmak için # kullanırız.
            let title = document.querySelector("#title");
            title.innerHTML = "Başlık Değişti";
            
            // Class ile arama yapmak için ise . kullanırız.
            let title = document.querySelector(".title");
            title.innerHTML = "Başlık Değişti";
            ```
            
        - Bunun dışında getElementsByClassName(), getElementsByTagName() veya getElementsByName() metodları da kullanılabilir.
    - Prompt İle Kullanıcıdan Veri Almak