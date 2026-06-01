# Homework Assignment

You have been assigned the task in [this (EN)](./assignment-en.md) document. / Az [ebben (HU)](./assignment-hu.md) a dokumentumban lévő feladatot szükséges megoldani.

Using GitHub actions, every diagram is rendered into a folder called `renders` on each branch, enabling easy documentation creation: by using the fully qualified name of the diagram (e.g., `Model.Drone.Package_Overview`), the render can be included in Markdown files:

![diagram](./renders/Model.Drone.Package_Overview.svg)

Use this method to create your documentation throughout the semester. Create a different Markdown file for each assignment in the `docs` folder. **The documentation should be sufficient for someone to understand your work, without opening any of the model files**.

We include an example model in `model.qeax` for ease of use. Treat this as a placeholder. Feel free to delete the model elements (or replace the file outright), but **keep the filename the same**.

The `main` branch is protected, and Pull Requests need to be opened for any updates. 

# Important links

* Tool usage Q&A: [https://q2a.inf.mit.bme.hu/](https://q2a.inf.mit.bme.hu/)
* Modeling tutorial: [https://ftsrg-rete.github.io/remo-lecture-notes/](https://ftsrg-rete.github.io/remo-lecture-notes/)
* Tool installation tutorial: [https://ftsrg-rete.github.io/remo-lecture-notes/rete-install-basics-en/](https://ftsrg-rete.github.io/remo-lecture-notes/rete-install-basics-en/)
* Markdown tutorial (for documentation): [https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)

# Házi feladat ellenőrző lista

Kötelező elemek:

- [ ] Rendszerkontextus
  - [ ] Kontextuselemek és tulajdonságaik azonosítása (BDD)
  - [ ] Kapcsolatok, adatáramlás és interfészek azonosítása (IBD)
- [ ] Követelmények
  - [ ] Érintettek összegyűjtése (UC)
  - [ ] Funkcionális és extrafunkcionális követelmények összegyűjtése, kidolgozása, modellezése (REQ)
  - [ ] Követelmények dekomponálása, később származtatása
- [ ] Használati esetek
  - [ ] Használati esetek összegyűjtése, modellezése (UC)
  - [ ] Használati esetek kidolgozása (elő- és utófeltételek, forgatókönyvek)
- [ ] Funkcionális modell/logikai architektúra
  - [ ] Fő funkciók összegyűjtése, dekomponálása (BDD)
  - [ ] Kapcsolatok, adatáramlás és interfészek azonosítása (IBD)
- [ ] Platform modell/fizikai architektúra
  - [ ] Fő platform komponensek összegyűjtése, komponálása, tulajdonságaik megadása (BDD)
  - [ ] Kapcsolatok, adatáramlás és interfészek azonosítása (IBD)
- [ ] Rendszerarchitektúra
  - [ ] Funkciók platformelemekre allokálása
  - [ ] Platformspecifikus funkciók modellezése (BDD)
  - [ ] Konfigurált platform elemek modellezése (BDD)
  - [ ] Komponens-funkció nézet (IBD)

- [ ] Hibatűrés: megfelelő hibatűrési minták az architektúra modellben
- [ ] Nyomonkövethetőség: A modellelemek között modellezni kell a nyomonkövethetőségi relációkat

Legalább egy viselkedésmodell:

- [ ] Interakció modellezése: Komponensek interakcóinak ábrázolása szekvenciadiagramon
- [ ] Folyamatmodellezés: Összetett folyamatok modellezése Activity Diagrammal
- [ ] Állapotgépek: Állapotgépek modellezése State Machine Diagramon

Legalább egy analízis módszer:

- [ ] Szolgáltatásbiztonsági analízis: Hibafa, eseményfa, vagy megbízhatósági blokkdiagram szolgáltatásbiztonság paramétereinek vizsgálatához
- [ ] Hibamód és -hatás analízis: részletes táblázatos FMEA a tervezés különböző fázisaiban a hibalehetőségek és hatásuk elemzésére
- [ ] Teljesítményanalízis: Teljesítménymodellezés és analízis egy teljesítmény követelmény teljesülésének bizonyításához
- [ ] Tesztelés és szimuláció: Egy vagy több funkcionális követelmény vizsgálata a funkcionális modellekhez készített tesztesetekkel és szimulációval
