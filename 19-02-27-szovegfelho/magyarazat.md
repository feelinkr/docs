# Szövegfelhő

Magyarázatok a 2019. február 27-i gyakorlaton felírt szövegfelhőhöz.

  * **Campaign**
    * A visszajelzéseket úgynevezett kampányok keretében gyűjtjük. Kampány lehet például:
      * hogyan érezték magukat az alkalmazottak X év Y. hetében?
      * mennyire tetszik a felhasználóknak az X szoftver Y verziója?
  * **Feedback**
    * Valamilyen kampányhoz valamilyen linken keresztül leadott visszajelzés.
  * **Links**
    * A visszajelzéseket linkeken keresztül gyűjtjük. A linkek tartalmaznak valamilyen payloadot, mely paramterizálja a visszajelzést.
  * **Timeslot**
    * Mind a Linkshez, mind a Feeadbackhez kapcsolódik. Mennyi ideig érvényes egy adott link?
  * **Encryption**
    * A linkek parametrizálását szimmetrikusan titkosítani kell, hogy ne lehessen átütni őket. Természetesen úgy kell titkosítani, hogy az eredményt linkbe lehessen pakolni -> base64.
  * **Email**
    * Ahelyett, hogy csak linkeket adnánk (van olyan opció is), lehetséges rajtunk keresztül kiküldeni a maileket is. Ehhez szükséges valamilyen külső szolgáltató (pl.: SendGrid, Amazon SES).
  * **Templating**
    * Az emailek template-ezhetők. Azaz nemcsak a feedback link parametrizálható, hanem az email is, amiben kimennek a linkek.
    * A kampányokra is létrehozhatók template-ek. Feltehető, hogy az X szoftver Y verzióját és az X szoftver Y+1 verzióját is azonos kampányon keresztül akarjuk kiértékelni. Ilyenkor hasznos egy kampány template.
    * **Markdown**: Lehetőség a felhasználóknak, hogy Markdownban definiáljanak template-eket.
  * **Tagging**
    * A sablonokhoz tagek rendelhetők.
  * **Open API**
    * A rendszerhez programatikus hozzáférést biztosítunk egy nyílt API-n keresztül.
  * **Event-based**
    * A kattintások lényegében egy streamet képeznek, melyre felhúzható egy szép event-based architektúra. Itt érdekes lehet a VoltDB vagy a Kafka.
  * **Authentication**
    * Az API felhasználóit valamilyen módon azonosítani kell. Erre szolgálhat **token-based authentication**.
  * **Pay-per-use**
    * Használat után kell fizetni, hasonlóan például a GCP-hez. Például minden kampány X$, aztán minden Y link Z$. Stb. 
  * **Analytics**
    * Analitikát biztosítunk, amivel bele lehet látni a kampányokba. Ehhez szükséges megfelelő lekérdezések definiálása, valamint analitikai dashboard biztosítása.
  * **Monitoring**
    * Nem lényeges, az analitikához kapcsolódik.
  * **Profiling**
    * Profilépítés a visszajelzések alapján. Ha van a linkek parametrizálásában valamilyen, felhasználóra utaló azonosító, akkor kampányokon átívelve össze lehet kötni akár, és profilt lehet hozzá építeni.
  * **Open Source (Apache-2.0)**
    * A szoftver nyílt forrású licenc alatt fejlesztjük. Maga a service, ami mi belövünk, persze fizetős.

Nem szerepel, de fontos:

  * Adatkezelési kérdések
    * Anonimizálás
    * Törlés
