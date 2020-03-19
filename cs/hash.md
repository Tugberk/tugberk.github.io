- hash fonksiyonları bir girdi alır, ve buna karşılık bir girdi çıkarırlar.
- girdinin kaç karakter olduğundan bağımsız olarak, belirli sayıda karakter içeren bir çıktı verir.

örneğin md5 hashing algoritmasına bakalım:
girdi: 123456
çıktı: e10adc3949ba59abbe56e057f20f883e

girdi: 123456ekleme
çıktı: 639bf53b247a53059a6e9ee03f4c3347

Görüldüğü gibi, girdiler birbirine benzese bile, çıktıların birbirine hiçbir benzerliği yok. Bununla birlikte, girdilerin uzunluğu değişse bile, çıktıların uzunluğu sabit kalıyor. Bu 5-10 karakterlik bir girdi değil, bir kitap bile olsa, aynı sayıda çıktı olacaktı.

Hash fonksiyonlarının birkaç özelliği var;

1. Farklı iki girdi sonucunda, aynı çıktıyı veremez.
2. Karakter sayısından bağımsız olarak verdiği çıktının karakter sayısı değişmez.
3. Çıktılardan yola çıkarak girdiler bulunamaz.

----

İnternet sitelerinin veritabanlarında şifreler saklanırken, açık şekilde saklanmazlar. Genellikle hash edilmiş halde saklarlar. Bunun nedeni, eğer veritabanı ele geçerse, şifreler direkt olarak ortaya çıkmasın diye. Ancak, sadece hash olarak saklamak da çok işe yaramayabilir.

Hash fonksiyonları bulunduğu zaman, birileri oturup bilgisayarları ile bilindik şeyleri hashleyerek bir tabloya yerleştirebilirler. Bu tabloya "rainbow table" adı verilir. Bu tabloya hashler verildiği zaman, otomatik olarak karşılığı bulunabilir. Çıktıların matematiksel olarak çevirisi yapılamasa da, bu şekilde yapılabilir. 

O yüzden, "salting" denilen, tuzlama denen bir işlem var. Siz kayıt olurken, siteyi kodlayan kişi tarafından belirlenen bir tuzlama işlemi uygulanır. Örneğin bu tuzlama basit bir şekilde, "fbook" olsun. O zaman şifreyi verdikten sonra (123456 şifre olsun); 123456fbook olacak. Bu tuzu da sadece siteyi kodlayan biliyor. Bu şekilde olup veritabanına konduğu zaman, veritabanı ele geçse bile, hali hazırda basit bir "rainbow table" ile çözülmesi güçleşecek. O yüzden en etkili yöntem odur.


Bunun dışında, gönderdiğimiz mesajların güvenli olup olmadığını, ya da bozulup/değişmediğini kontrol etmek için kullanılabilir. Örneğin ben bir kişiye mail attım. Ardından o maili hashledim ve bu hash'i, arkadaşıma Whatsapp / elden bir yolla gönderdim. Şimdi o mail o kişiye gelince, kendisi de aynı hash fonksiyonuna sokuyor maili. Eğer mail değişmediyse, hash aynı olmalı. Bu da basit bir test yöntemi.
