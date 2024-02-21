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
