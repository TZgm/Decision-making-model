Real Estate Selection OptimizerEz a projekt egy R-alapú döntéstámogató modell, amely segít kiválasztani a legoptimálisabb budapesti lakásokat több mint 500 hirdetés közül. 
A cél a szubjektív szempontok és a matematikai rangsorolás ötvözése a legjobb ár-érték arányú befektetés megtalálásához.

📌 Projekt háttérA modell alapjául az ingatlan.com oldalról (MS Power Query segítségével) letöltött ~500 hirdetés szolgál. A manuális válogatást egy objektív, súlyozott rangsorolási algoritmus váltja fel, amely figyelembe veszi a személyes preferenciákat is (pl. kerületi prioritások).

🛠 Adatfeldolgozás és Módszertan1. Előkészítés és TisztításSzűrés: Csak a minimumfeltételeknek megfelelő lakások megtartása (Ár <= 60M Ft, Szobák száma >1).Lokáció preferenciák: A kerületek kategorizálása (XIII. és IV. kerület kiemelt előnyben).
Döntési szempontok: Ár, Négyzetméterár, Terület, Szobák száma, Kerületi preferencia.
2. Rangsorolási technikákA projekt három szinten finomítja az eredményeket:Egyszerű rangsorolás: Minden paraméterre külön sorrend felállítása, majd összesítés.Normalizáció: Az adatok skálázása ($v_i = a_i / \max(a_i)$), hogy a különböző mértékegységek összehasonlíthatóak legyenek.
Súlyozott döntési mátrix: A szempontok fontossági sorrendbe állítása (legnagyobb súllyal a négyzetméterár és a lokáció szerepel).3. VizualizációA modell ggplot2 és ggrepel segítségével vizualizálja a lakások közötti eltéréseket, segítve a "Pareto-optimális" választások azonosítását.

📊 EredményekA modell sikeresen leszűkítette az 500 elemű listát a top 10 legígéretesebb ingatlanra. Az elemzés rávilágított, hogy:
A súlyozott és a sima rangsorolás 80%-os átfedést mutat (8 ingatlan mindkét listán szerepel).A legjobb választások jellemzően a XIII. kerület (Lőportár utca, Teve utca, Kassák Lajos utca) környékén összpontosulnak.

💻 HasználatA kód futtatásához szükséges R csomagok:Rinstall.packages(c("readxl", "tidyverse", "reshape2", "DT", "ggrepel"))
A munkafolyamat:Töltsd be az ingatlanok.xlsx fájlt.Futtasd a szűréseket a saját anyagi keretedre szabva.Módosítsd a d_weights vektort a saját prioritásaid szerint.
