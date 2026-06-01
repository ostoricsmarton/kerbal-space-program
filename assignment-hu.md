# Küldetési kontextus és feladatleírás

## Háttér

Egy európai egyetemi kutatási konzorcium kis méretű műholdak sorozatát tervezi felbocsátani kereskedelmi hordozórakéták fedélzetén, **másodlagos hasznos teherként (secondary payload)**.

Ezek a műholdak a **CubeSat szabványt** követik, amely széles körben alkalmazott, költséghatékony űrmissziós megközelítés egyetemek, startup vállalatok és kutatóintézetek számára.

A CubeSatok szabványos méretű egységekből („U”) felépülő moduláris nanoszatellitek. Egy egység (1U) egy körülbelül **10 × 10 × 10 cm-es kockának** felel meg. A feladat során minden csapat egy **3U CubeSatot** tervez, vagyis egy körülbelül három egység hosszúságú űreszközt.

A konzorcium célja annak demonstrálása, hogy egy viszonylag kis mérnökcsapat modern **modellalapú rendszermérnöki (Model‑Based Systems Engineering – MBSE)** módszerekkel képes komplex űrrendszerek tervezésére.

A hallgatói csapatok szerződött rendszermérnöki csoportként működnek, és egy adott műholdküldetés architektúrájának meghatározásáért felelősek.

A feladat célja nem az űrmérnöki specializáció megszerzése, hanem a következők gyakorlása:

*   követelmények értelmezése,
*   architekturális döntéshozatal,
*   viselkedési modellezés,
*   nyomonkövethetőség (traceability),
*   valamint mérnöki indoklás korlátozások mellett.

Amennyiben az információk hiányosak, **ésszerű mérnöki feltételezések** alkalmazhatók, feltéve hogy ezek explicit módon dokumentálva vannak a modellben.

## Küldetés áttekintése

Minden csapat egy kijelölt küldetésváltozatot kap.

Bár a küldetések technikai alapjai hasonlóak, működési prioritásaik és az érintett szereplők (stakeholderek) elvárásai eltérnek.

A műhold **alacsony Föld körüli pályán (Low Earth Orbit – LEO)** működik, jellemzően **450–600 km** magasságban.

Ezen a pályán a műhold minden keringés során többször belép a Föld árnyékába, majd visszatér napfénybe. Ezek az **árnyékos (eclipse) periódusok** korlátozzák az energiatermelést, és jelentősen befolyásolják az üzemeltetési tervezést.

A várható működési élettartam körülbelül **18–36 hónap**.

A műholdnak nagyrészt autonóm módon kell működnie, mivel a földi operátorokkal való kommunikáció csak rövid időablakokban lehetséges, amikor a műhold egy földi állomás fölé kerül.

## Küldetés: Rádiós hálózati csomópont (Radio Network Node – RN)

Ez a küldetés kommunikációs reléként működik.

A műhold rádióüzeneteket fogad földi felhasználóktól vagy szenzoroktól, ideiglenesen eltárolja őket, majd később továbbítja, amikor megfelelő letöltési (downlink) lehetőség adódik.

Tipikus kihívások:

*   vevő rendelkezésre állásának összehangolása a korlátozott energiaforrásokkal,
*   üzenettárolás kezelése,
*   rádiókommunikációs szabályozások betartása.

## Platformkoncepció

A küldetés típusától függetlenül a műhold két fő részből áll:

1.  **Műholdplatform (Satellite Bus / Platform)** – az űrbeli működéshez szükséges újrafelhasználható infrastruktúra.
2.  **Hasznos teher (Payload)** – a küldetés célját megvalósító berendezés.

A hallgatóknak olyan architektúrát kell tervezniük, amely a rendszerfunkciókat például az alábbi elemekhez rendeli:

*   fedélzeti számítógép (On‑Board Computer – OBC),
*   elektromos energiaellátó alrendszer (Electrical Power System – EPS),
*   kommunikációs rádiók,
*   szenzorok és aktuátorok,
*   adattárolás,
*   payload interfészek.

Elvárás a kereskedelmi forgalomban elérhető CubeSat komponensek használata, ahol lehetséges.

A konkrét hardverválasztás később nyilvánosan elérhető beszállítói katalógusok alapján becsülhető.

A feladat fókusza az architektúratervezés, nem a részletes hardvertervezés.

## Üzemeltetési elvárások

Az űreszköznek:

*   túl kell élnie a felbocsátást és a kibocsátást,
*   autonóm módon kell működnie földi kapcsolat nélkül,
*   biztonságos üzemi állapotokat kell fenntartania,
*   végre kell hajtania a küldetés feladatait,
*   valamint támogatnia kell a távoli monitorozást és vezérlést.

A hallgatóknak modellezniük kell:

*   funkcionális bontást,
*   funkciók alrendszerekhez rendelését,
*   üzemmódokat,
*   valamint kiválasztott viselkedési aspektusokat (pl. ütemezés, hibakezelés, működési munkafolyamatokat).

A viselkedési modellek lehetnek:

*   állapotgépek (state machine),
*   aktivitásdiagramok,
*   szekvenciadiagramok.

A csapatoknak verifikációs megközelítéseket is definiálniuk kell, és legalább egy mérnöki szempont (biztonság, megbízhatóság, teljesítmény vagy funkcionális helyesség) elemzését bemutatniuk.

## Fontos fogalmak

**Hasznos teher (Payload)**

A műhold elsődleges feladatát végrehajtó berendezés (kamera, rádiós relé vagy kísérleti modul).

**Műholdplatform (Satellite Bus / Platform)**

A küldetéstől független működéshez szükséges alrendszerek, például energiaellátás, számítástechnika és kommunikáció.

**Alacsony Föld körüli pálya (Low Earth Orbit – LEO)**

A Földhöz viszonylag közeli pálya, ahol a műhold rendszeresen a Föld árnyékába kerül.

**Földi állomás (Ground Station)**

Földfelszíni kommunikációs létesítmény parancsok küldésére és telemetria, valamint küldetéssel kapcsolatos adatok fogadására.

**Telemetria (Telemetry)**

A műhold állapotinformációi, például hőmérséklet vagy akkumulátorállapot.

**Parancsküldés (Commanding)**

A földi operátorok által küldött utasítások.

**Biztonsági üzemmód (Safe Mode)**

Hiba esetén aktiválódó védelmi konfiguráció, amelyben a nem létfontosságú funkciók leállnak.

**Kereskedelmi polcról elérhető komponensek (Commercial Off‑The‑Shelf – COTS)**

Szabványos, kereskedelmi termékek egyedi fejlesztés helyett.

**Másodlagos hasznos teher (Secondary Payload)**

Elsődleges küldetéssel együtt indított űreszköz, amelynek szigorú biztonsági követelményeknek kell megfelelnie.

## Mérnöki feltételezések

A hallgatóktól nem elvárt speciális űrmérnöki háttértudás.

A csapatok:

*   alkalmazhatnak ésszerű feltételezéseket,
*   egyszerűsíthetik a pályamechanikai modelleket,
*   vagy meghatározhatnak hiányzó numerikus paramétereket.

Minden feltételezésnek dokumentáltnak és nyomonkövethetőnek kell lennie a modellben.

A cél egy koherens és jól indokolt architektúra, nem a technikai tökéletesség.

# Stakeholder inputok

## Megbeszélési jegyzőkönyvek és kivonatok

Az alábbi kivonatok a CubeSat programban részt vevő szervezetek képviselőivel folytatott egyeztetések összefoglalói. A jegyzeteket projektkoordinátorok készítették, ezért informális megfogalmazásokat, feltételezéseket vagy részleges nézőpontokat is tartalmazhatnak. A vezető rendszermérnök a feljegyzéseket átvizsgálta, és további megjegyzéseket, illetve iránymutatásokat fűzött hozzájuk.

A hallgatói csapatok feladata az érintett szereplők (stakeholderek) azonosítása, az aggályok és elvárások értelmezése, valamint ezek formalizálása követelményekké.

## Memo A: Programfinanszírozási Meeting

Reális elvárásokat kell megfogalmaznunk. A cél ismételhető küldetések demonstrálása, nem egyedi mérnöki kutatási projektek létrehozása. Ha minden csapat saját elektronikát tervez, a költségek gyorsan elszabadulnak, és az integráció kezelhetetlenné válik.

Lehetőleg meglévő CubeSat modulokat szeretnénk használni. A beszállítók már kínálnak avionikai rendszereket, rádiókat, energiaellátó alrendszereket stb. Ezek használata az alapértelmezett, kivéve ha nagyon erős szakmai indok szól ellene.

Ne felejtsük el, hogy ez egy kis műhold. Nem finanszírozunk redundáns rendszereket, hacsak valaki egyértelműen nem tudja megindokolni, hogy a küldetés másként kudarcot vallana. A teljes hardverköltségnek egy egyetemi projekt léptékén kell maradnia – jóval a nagy kutatási műholdak költségszintje alatt.

**_Vezető mérnök megjegyzései:_**

*   _Előnyben részesítendők a kereskedelmi CubeSat alrendszerek (OBC, EPS, rádiók, szenzorok)._
*   _Tipikus alrendszerköltség: kb. 5 000–40 000 €._
*   _3U küldetésekben a hardverredundancia ritka; szoftveres helyreállítás jellemzőbb._
*   _Teljes hardverköltség nagyságrendi feltételezésként ≈ 200 000 €._

## Memo B: Launch Integration Koordinációs Meeting

Az indítási közvetítő ismét hangsúlyozta, hogy a másodlagos hasznos terhek csak addig elfogadhatók, amíg kiszámíthatóan viselkednek. Bármilyen veszélyes helyzet az egész indítási kampányt késlelteti.

A műholdnak szabványos deployerbe kell illeszkednie. Ne feltételezzenek extra térfogatot vagy kiálló elemeket, kivéve ha azok indításkor rögzített állapotban vannak.

A legnagyobb aggodalom az idő előtti aktiváció. A rádiók vagy más elektromos rendszerek korai bekapcsolása elfogadhatatlan. Egyértelmű átmenetnek kell lennie az indítási konfiguráció és a kibocsátás utáni működési konfiguráció között.

Feltételezhető kibocsátási visszajelző jel vagy időzítő, mielőtt bármilyen aktív működés megkezdődik.

**_Vezető mérnök megjegyzései:_**

*   _Szabványos 3U méret: kb. 10 × 10 × 34 cm._
*   _Indításkor nem lehetnek kiálló elemek; deployálható szerkezetek később aktiválhatók._
*   _Többszörös deployment inhibit várható (mechanikai kapcsoló + időzítő vagy szoftverfeltétel)._
*   _RF adás csak kibocsátás után, több tíz perces késleltetéssel indulhat._

## Memo C: Szabályozói konzultáció

A frekvencialicenc kötelező. A rádió üzemeltetőjének képesnek kell lennie az adási paraméterek konfigurálására az engedélyezett frekvenciakiosztásnak megfelelően.

Hosszú távú űrszemét‑kezelési aggályokról is szó esett. Még a kis műholdaktól is elvárt a felelős viselkedés a küldetés végén. Senki sem szeretne ellenőrizetlenül működő adókat vagy részben aktív rendszereket a pályán hagyni.

A műholdnak lényegében „rendbe kell tennie maga után”, amikor a működés befejeződik.

**_Vezető mérnök megjegyzései:_**

*   _A rádió paraméterei (frekvencia, adóteljesítmény, beacon periódus, adatsebesség) parancsokkal konfigurálhatók legyenek._
*   _LEO pályán a passzív légköri fékeződés elfogadható deorbit megoldás._
*   _Küldetés végén adólekapcsolás és akkumulátor passziválás szükséges._

## Memo D: Workshop a földi üzemeltetéssel

Az operátorok nem tudják folyamatosan felügyelni a műholdat. A földi állomás áthaladások rövidek, és néha teljesen elmaradnak.

Rendszeres állapotinformációra van szükségünk, hogy tudjuk, a műhold életben van‑e. Már néhány óránként egy rövid jelentés is sokat segítene.

Ha a műhold energiatakarékosság miatt kihagy egy jelentést, szeretnénk érteni az okát. Ellenkező esetben a hibakeresés csak találgatás.

A parancsküldési képesség szintén alapvető. A parancsokat nem lehet ellenőrzés nélkül elfogadni – hibák történnek, és az illetéktelen adások valós kockázatot jelentenek. Szükség van hitelesítésre és fogadott parancsok naplózásra.

A küldetés során szoftverfrissítések várhatók. Az egyetemek gyakran fedeznek fel javításokat indítás után. Ha azonban egy frissítés hibás, a műholdnak automatikusan helyre kell állnia.

**_Vezető mérnök megjegyzései:_**

*   _Feltételezhető napi 2–4 földi kapcsolat, egyenként kb. 5–10 perc._
*   _A műhold néhány óránként rövid állapotjelző beacon telemetriát sugároz (alapvető energia-, termikus-, és működésiállapot-információk). A beacon célja a robusztus működés, nem a magas adatsebesség._
*   _Parancshitelesítés szükséges._
*   _Frissítés utáni visszaállási (fallback) mechanizmus elvárt._

## Memo E: Megbízhatósági és biztonsági egyeztetés

Az űreszközök gyakran azért hibásodnak meg, mert kis problémák láncreakcióvá alakulnak. Egy hőmérsékleti kiugrás vagy akkumulátorprobléma nem jelentheti azonnal a küldetés végét.

Szükség van egy konzervatív konfigurációra, amelyben a műhold csak a túlélésre és a Földdel való kommunikációra koncentrál.

Az akkumulátorok különösen érzékenyek. A mélykisütés az egyik leggyakoribb meghibásodási ok.

A számítógépek is lefagyhatnak – a sugárzás valós jelenség. Helyreállítási mechanizmusokra szükség van, még ha egyszerű reset is az.

**_Vezető mérnök megjegyzései:_**

*   _Hibák esetén előnyben részesítendők az üzemmódváltások._
*   _Safe Mode letiltja a payloadot és nagy teljesítményű adókat._
*   _Mélykisütés maradandó akkukárosodást okoz._
*   _Watchdog vagy reset helyreállítás tipikus._

## Memo F: Mechanikai és integrációs egyeztetés

A payload csapatok gyakran változnak, ezért az interfészek ne igényeljenek újratervezést minden alkalommal. Ideális esetben kiszámítható elektromos és mechanikai interfészen keresztül csatlakoznak.

Az operátorok azt is megkérdezték, lehet‑e távolról kapcsolni a payload tápellátását. Ez megkönnyítené a hibásan működő kísérletek kezelését.

**_Vezető mérnök megjegyzései:_**

*   _Standardizált tápellátási sínek és adatkapcsolat (pl. soros vagy CAN szerű)._
*   _Payload tápellátás kapcsolása a fedélzeti számítógép által._

## Memo G: Termikus és energiaellátási konzultáció

Az űrbeli hőmérséklet‑ingadozás jelentős. A napfény gyorsan felmelegíti a műholdat, az árnyék pedig gyors lehűlést okoz. A szenzorok önmagukban nem elegendők – a határértékek közelében valaminek be kell avatkoznia.

Az energiaellátási tartalékok szintén kritikusak. Árnyékban nincs energiatermelés, ezért a terheléseket kezelni kell.

**_Vezető mérnök megjegyzései:_**

*   _Belső üzemi hőmérséklet célérték: −10 °C – +50 °C._
*   _Termikus reakció lehet fűtés vagy payload leállítás._
*   _Árnyékidő: kb. 30–40 perc egy ~95 perces keringés során._
*   _Energiaprioritás és költségvetés szükséges._

## Memo H: Verifikációs tervezési megbeszélés

Nem érdekelnek bennünket az ellenőrizhetetlen architektúra‑ábrák. A csapatoknak gondolniuk kell arra, hogyan bizonyítanák a rendszer működését.

Már az egyszerű verifikációs gondolkodás is segít – teszt, ellenőrzés vagy analízis formájában.

A követelmények és a tervezési elemek közti nyomonkövethetőség legyen látható.

**_Vezető mérnök megjegyzései:_**

*   _Verifikációs módszer korai meghatározása ajánlott._
*   _Követelmény–architektúra nyomonkövethetőség elvárt._

## Memo I: Rádiós hálózati ügyfél

A felhasználók elvárják, hogy a műhold elég gyakran figyeljen. Ha túl sokat alszik, a relészolgáltatás értelmetlenné válik.

A rádiós szabályozók korlátozásokat alkalmaznak, és ezek betartását igazolni kell.

Az üzenetek nem veszhetnek el csak azért, mert a műhold nem tudja azonnal továbbítani őket.

**_Vezető mérnök megjegyzései:_**

* _A tipikus CubeSat UHF vevők aktív állapotban körülbelül 1–2 W teljesítményt fogyasztanak, ami összemérhető az alap avionikai rendszerek energiaigényével. A folyamatos vétel ezért nem jellemző; az elérhető energia függvényében 10–50 %-os vevő duty cycle feltételezése ésszerű (25 % esetén ez egy 95 perces keringés alatt körülbelül 9–10 perc vételi időt jelent)._

* _A bejövő forgalom bármikor érkezhet amikor a műhold éppen figyel (vételi üzemmódban van), jellemzően 9,6–19,2 kbps adatsebességgel, rövid burst jellegű adások formájában. Az egyedi felhasználói üzenetek vagy telemetriai csomagok általában néhány száz byte és néhány kilobyte közötti méretűek, és ugyanazon pályaáthaladás során több felhasználó is adhat._

* _A földi kommunikációs lehetőségek korlátozottak; ésszerű feltételezés naponta körülbelül három földi állomás kapcsolat, kapcsolatonként 5–10 perc hasznos adatkapcsolati idővel. 19,2 kbps adatsebesség és körülbelül 70 %-os hatásos adatátviteli arány mellett a teljes napi letöltési (downlink) kapacitás mindössze néhány megabyte lehet._

* _Időjárási vagy üzemeltetési problémák akár 72 órán keresztül is megakadályozhatják a sikeres letöltést. Ennek megfelelően a tartós fedélzeti adattárolást úgy kell méretezni, hogy több napnyi felhalmozódó adatforgalmat, beleértve az üzemeltetési naplókat is, képes legyen kezelni._
