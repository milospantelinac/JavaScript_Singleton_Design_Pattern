# JavaScript - Singleton Design Pattern

Singleton Patern ograničava broj instanci određenog objekta na samo jednu. Ova pojedinačna instanca naziva se singleton.

## Upotreba Singletona

Singleton je koristan u situacijama u kojima je potrebno koordinisati radnje celog sistema s jednog središnjeg mjesta. Primer je skup veze baze podataka. Skup upravlja stvaranjem, uništavanjem i vekom trajanja svih veza baze podataka za celu aplikaciju osiguravajući da se nijedna veza ne izgubi. 

Nekoliko drugih paterna, kao što su Fectory, Prototip i Fasada, često se implementiraju kao Singletoni kada je potrebna samo jedna instanca.

## Diagram 

<img width="200" alt="singleton_diagram" src="https://user-images.githubusercontent.com/21141150/205888517-0f166a8c-1e08-4898-860d-b44c6e820d6e.png">

## Učesnici

Objekti koji učestvuju u ovom paternu su:

**Singleton** -- U primeru: SpaceX
- definiše getInstance() koja vraća jedinstvenu instancu.
- odgovoran za stvaranje i upravljanjem objektom instance

## Primer

Objekat **SpaceX** implementiran je kao neposredna anonimna funkcija. Funkcija se odmah izvršava wrepovanjem u zagradi nakon kojih slede dve dodatne zagrade. Zove se anonymous, jer nema ime ([Self-Invoking Functions](https://www.w3schools.com/js/js_function_definition.asp#:~:text=Self%2DInvoking%20Functions,self%2Dinvoke%20a%20function%20declaration.)).

Metoda **getInstance** je deo SpaceX-a objekta koji vraća jednu instancu objekta dok zadržava privatnu referencu na njega koja nije dostupna public wolrd-u.

Metoda **getInstance** demonstrira još jedan dizajn patern koji se zove **Lazy Load**. Lazy Load proverava je li instanca već stvorena; ako nije, stvara ga i storuje za buduću upotrebu. Svi sledeći pozivi primit će storuje instancu. Lazy Load je tehnika uštede procesora i memorije stvaranjem objekata samo kada je to apsolutno neophodno.

```
var SpaceX = (function () {
    var instance;

    function createInstance() {
        var object = new Object("Ja sam SapceX instanca!");
        return object;
    }

    return {
        getInstance: function () {
            if (!instance) {
                instance = createInstance();
            }
            return instance;
        }
    };
})();

var instance1 = SpaceX.getInstance();
var instance2 = SpaceX.getInstance();

console.log("Da li je ista instanca? " + (instance1 === instance2));
```


