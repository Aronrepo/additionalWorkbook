# Web Module Questions

### 1.

### Mit nevezünk cloudnak?

A "cloud" vagy "felhő" kifejezés általában az interneten keresztül elérhető távoli számítási erőforrásokat és szolgáltatásokat jelenti. A "felhő" általában a következő típusú szolgáltatásokat foglalja magában:

- Infrastruktúra felhő (Infrastructure as a Service - IaaS): Olyan szolgáltatás, amely lehetővé teszi a felhasználók számára a számítási infrastruktúra - például szerverek, hálózatok, tárolók - virtuális formában történő bérlését és használatát.

- Platform felhő (Platform as a Service - PaaS): Olyan szolgáltatás, amely fejlesztőknek és vállalatoknak lehetőséget biztosít arra, hogy alkalmazásaikat és szolgáltatásaikat egy előre elkészített fejlesztési platformon keresztül hozzák létre és üzemeltessék, például az alkalmazásfejlesztéshez szükséges eszközök és környezet biztosításával.

- Szoftver felhő (Software as a Service - SaaS): Olyan szolgáltatás, amelyben a szoftvereket felhőalapú módon biztosítják, és a felhasználók ezeket az interneten keresztül érik el, például e-mail szolgáltatások vagy irodai alkalmazások.

Néhány kulcsfontosságú jellemzője a felhőtechnológiának:

- **On-demand self-service:** A felhasználók igény szerint biztosíthatnak erőforrásokat, például tárolót, feldolgozási kapacitást és alkalmazásokat, anélkül, hogy emberi beavatkozásra lenne szükség a szolgáltató részéről.

- **Broad network access:** A felhőszolgáltatások elérhetők az interneten keresztül különféle eszközökről, ideértve a okostelefonokat, táblagépeket, laptopokat és asztali számítógépeket.

- **Resource pooling:** A felhőszolgáltatók számítási erőforrásokat összevonják több ügyfél számára, lehetővé téve számukra, hogy dinamikusan kiosszák az erőforrásokat az igények szerint. Ez segít az erőforrásfelhasználás és a skálázhatóság optimalizálásában.

- **Rapid elasticity:** A felhőszolgáltatások gyorsan növelhetők vagy csökkenthetők az igények változásának kielégítése érdekében. Ez lehetővé teszi a felhasználók számára, hogy könnyen növeljék vagy csökkentsék erőforrásfelhasználásukat igényeiknek megfelelően.

- **Measured service:** A felhőszolgáltatások általában mértek, azaz a felhasználók csak az általuk fogyasztott erőforrásokért fizetnek. Ez a fizet-ahogy-használod modell költségmegtakarítást eredményezhet a hagyományos IT-infrastruktúrához képest, ahol az erőforrásokat előre biztosítják.

Ezek a felhőszolgáltatások lehetővé teszik a felhasználók számára, hogy a számítási erőforrásokat rugalmasan, skálázható módon és gyakran fizetési modell alapján használják, ami általában lehetővé teszi a költségek csökkentését és az erőforrások hatékonyabb kihasználását.

### 2.

### Miből áll egy JWT token?

Egy JWT (JSON Web Token) három részből áll, melyeket pontokkal vannak elválasztva:

**Header (Fejléc):** Ez a token típusát és az alkalmazott algoritmust tartalmazza. Általában ez JSON formátumú, és tartalmazza a token típusát (typ), valamint az alkalmazott algoritmus leírását (alg). Például:

<pre><code>
{
  "typ": "JWT",
  "alg": "HS256"
}
</code></pre>

**Payload (Tartalom):** Ez a JWT ténylegesen használt adatokat tartalmazza, mint például a felhasználó azonosítója, jogosultságok vagy egyéb információk. Ez is JSON formátumban van, és tetszőlegesen kibővíthető a szükséges adatokkal. Például:

<pre><code>
{
  "sub": "1234567890",
  "name": "John Doe",
  "admin": true
}
</code></pre>

**Signature (Aláírás):** Ez a token digitális aláírása, amelyet a fejléc és a tartalom alapján hoznak létre, és titkosítják a kibocsátó által használt kulcs segítségével. Az aláírás a token validitásának ellenőrzésére szolgál, és biztosítja, hogy a token tartalma nem változik meg. Például:

<pre><code>
HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  secret
)
</code></pre>

Az összes részt pontokkal választják el egymástól, így egy JWT tokennek a következő formátuma van:

<pre><code>
header.payload.signature
</code></pre>

Fontos megjegyezni, hogy a JWT tokenek alapvetően nem titkosítottak, csak aláírva vannak. Ez azt jelenti, hogy a token tartalma könnyen olvasható, ha valaki hozzáfér hozzá, ezért ne tároljon érzékeny adatokat a JWT tartalmában, különben azok bárki számára hozzáférhetővé válhatnak. Titkosításhoz külön lépéseket kell tenni.

### 3.

### Mi az a normalizálás, mi az 1, 2, 3. normálforma?

Az adatbázisoknál a normalizálás egy adatbázis tervezési eljárás, amelynek célja az adatok redundanciájának csökkentése és az adatbázis strukturális integritásának javítása.

**1NF:**
Az adatok első normálformában való elhelyezése az egyik alapvető lépés a relációs adatbázisok tervezése során. A normálformák hierarchiájában az első normálforma (1NF) azt jelenti, hogy egy adatbázis táblájában minden attribútum csak egyetlen értéket tartalmaz egy adott oszlopban és egy adott sorban.

Más szóval az első normálforma azt követeli meg, hogy minden cellában csak egy elem legyen jelen, tehát ne legyen többértékű attribútum vagy lista. Ha egy attribútum több értéket tartalmaz, akkor azt úgy kell felbontani, hogy minden érték külön oszlop legyen.

Például, ha egy "Könyv" táblában szerepel egy "Szerző" attribútum, és egy könyvnek több szerzője van, akkor az első normálforma értelmében nem lehet egy oszlopban felsorolni a szerzőket vesszővel elválasztva. Ehelyett minden szerzőt külön oszlopba kell szétválasztani, vagy egy külön "Szerző" táblába kell helyezni, és azonosítókkal kell hivatkozni rájuk.

**2NF:**

A második normálforma akkor érhető el, amikor egy tábla minden nem elsődleges attribútuma teljes mértékben funkcionálisan függ a teljes elsődleges kulcstól

Például, ha Player_Inventory táblában van egy Player_ID elsődleges kulcs, akkor a Palyer_rating nem elsődleges kulcs minden egyes sora függ az elsődleges kulcstól.

**3NF:**

A 3NF célja, hogy minden adat csak egyetlen helyen legyen tárolva az adatbázisban, és hogy minden nem-kulcs attribútum kizárólag a kulcsoktól függjön.

Például, ha az előző Player_Inventory táblában behozok egy skill level és rating olszopot. Ekkor bár ezek külön-külön függnek a kulcstól, de rating függ a level-től. Ilyenkor érdemes külön táblában tárolni az egyes levelkhez tartozó ratinget.

### 4.

### ACID

**Atomitás (Atomicity):** Egy tranzakció vagy teljesen megtörténik, vagy egyáltalán nem. Ez azt jelenti, hogy ha egy tranzakció több lépésből áll, az csak akkor lesz végrehajtva, ha minden lépése sikeres. Ha bármelyik lépés sikertelen, akkor a tranzakció visszavonásra kerül, és az adatbázis visszakerül az eredeti állapotba.

**Konzisztencia (Consistency):** == Correctness. Az adatbázisnak minden tranzakció után konzisztens állapotban kell lennie. Ez azt jelenti, hogy a tranzakciók végrehajtása során az adatbázisba bevitt változtatásoknak meg kell felelniük minden meghatározott üzleti szabálynak és adatintegritási megkötésnek. Például, ha meg van határozva egy constraint, akkor annak igaznak kell lennie a tranzakció után is.

**Izoláció (Isolation):** Különböző tranzakciók egymástól való elkülönítettségét jelenti. Ez biztosítja, hogy a tranzakciók párhuzamos végrehajtása esetén ne zavarjanak egymást, és ne vezessenek inkonzisztens állapotokhoz az adatbázisban. Az izoláció biztosítja a tranzakciók által egyszerre elérhető adatok integritását.

**Tartósság (Durability):** Ez a tulajdonság azt jelenti, hogy a tranzakciók végrehajtása után az adatok maradéktalanul és véglegesen eltárolódnak az adatbázisban, még akkor is, ha a rendszer esetleg hibás vagy leáll. A tartósság biztosítja, hogy az adatok ne vesszenek el a rendszer hibája vagy leállása esetén.




