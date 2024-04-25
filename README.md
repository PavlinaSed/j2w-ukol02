# Task 2

The goal is to create a web page that displays a randomly selected quote and a randomly selected image every time it loads. The page might look something like this
(there are stylesheets in the project), but there are no limits to your creativity:

![screenshot](screenshot.jpg)

1. Use this repository as a template from which to create a repository in your GitHub account.
1. Clone the repository **from your GitHub account** to your local machine.
1. Launch the cloned application and open the [http://localhost:8080/](http://localhost:8080/) page in your browser. You will see a page with a single quote and
   image. However, the page is static, nothing changes when the page is refreshed.
1. Edit the page to make it dynamic - so that the text and image change randomly each time it loads.
1. Check the result in your browser.
1. *Commit* and *push* the changes (the resulting code) to your GitHub repository.
1. Post a link to your repository as a solution to the challenge on [My Czechitas](https://moje.czechitas.cz).

## Could be useful

For example, you can use [Unsplash](https://unsplash.com) as a source of images - a site with images and photos [free](https://unsplash.com/license). You can get images from it
download them to your app or link them directly from their site. If you want to link directly to a photo with the code `XXX` (the code is the 10 characters at the end of the URL)
of the photo), you can use the following link:

```
https://source.unsplash.com/XXX
https://source.unsplash.com/XXX/1600x900
```

The second option specifies the desired dimensions of the image - if the image has a different aspect ratio, it will be cropped to the desired aspect ratio. The exact dimensions of the user's screen
But don't worry - the image is stretched or shrunk using CSS to cover the entire page.

You can use the `src/main/resources/citaty.txt` file, which is part of the downloaded project, as a source for the quotes.

### Random numbers

The [Random] class(https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/Random.html) is used to generate random numbers in Java.

### Reading a text file from *resources*

Code to load the lines of a file in *resources* into a list of strings (`List<String>`):

```java
private static List<String> readAllLines(String resource)throws IOException{
    //Resource files are retrieved using the classloader. First we need to get the current classloader.
    ClassLoader classLoader=Thread.currentThread().getContextClassLoader();

    //Using the getResourceAsStream() method, we get the InpuStream from the classloader that reads from the corresponding file.
    //Next we convert the InputStream to BufferedRead, which reads text in UTF-8 encoding 
    try(InputStream inputStream=classLoader.getResourceAsStream(resource);
        BufferedReader reader=new BufferedReader(new InputStreamReader(inputStream,StandardCharsets.UTF_8))){

    //Method lines() returns a stream of lines from the file. Use the collector to convert Stream<String> to List<String>.
    return reader
        .lines()
        .collect(Collectors.toList());
    }
}

// example call: readAllLines("citaty.txt")
```
### Creating a list of text strings directly in Java source code

If I want to create a list of several text strings and I don't want them in an external file, I can use the `List.of()` method:

```java
List<String> listTextu=List.of("string 1", "string 2", "another string", "yet another string");
```

### Inline style background image

Cascading Style Sheets (CSS) can also be written as *inline styles* - the relevant CSS code is listed right next to the HTML element to which it applies, specifically in the attribute
`style`. So the following HTML code will create a `div` that will have the background color set to red.

```html

<div style="background-color: red">This text has a red background color.</div>
```

### Inserting HTML instead of plain text via Freemarker

When the `${text}` interpolation is used in Freemarker, the contents of the `text` variable are inserted into the page so that the browser displays exactly what is in the text.
That is, if it contains any HTML tags, those tags will be displayed on the page in text, e.g. `<div>`.
If you want to insert text as HTML, you need to use `${text?no_esc}` (i.e. no escaping, i.e. replacing characters with special meaning).
**Warning, code pasted in this way is not checked in any way.
Therefore, you should only insert HTML code in this way that you trust.
Under no circumstances should you insert user-supplied code in this way.
The user could, for example, slip a `<script>` tag into the code and run whatever code they want in the browser.**

### Links

* Link to [Lesson 2](https://java.czechitas.cz/2024-jaro/java-2-online/lekce-2.html)
* Java SE 21 [Javadoc](https://docs.oracle.com/en/java/javase/21/docs/api/java.base/)- documentation of all the classes that are part of the base Java version 21.
* Documentation [Spring Boot](https://spring.io/projects/spring-boot#learn) - from here the annotation `@SpringBootApplication` and the class `SpringApplication`.
* The [Spring Framework](https://spring.io/projects/spring-framework#learn) documentation - from here are the `@Controller`, `@GetRequest` annotations and the `ModelAndView` class.
* Documentation [Freemarker](https://freemarker.apache.org/docs/index.html) - the templating system for HTML used in the project.
* [Unsplash](https://unsplash.com) - free images and photos to use

# Úkol 2

Cílem je vytvořit webovou stránku, která při každém načtení zobrazí náhodně zvolený citát a náhodně zvolený obrázek. Stránka může vypadat nějak takhle
(v projektu jsou k tomu připravené styly), ale fantazii se meze nekladou:

![screenshot](screenshot.jpg)

1. Použij toto repository jako šablonu (Use this template), ze které si vytvoříš repository ve svém účtu na GitHubu.
1. Naklonuj si repository **ze svého účtu** na GitHubu na lokální počítač.
1. Spusť si naklonovanou aplikaci a otevři v prohlížeči stránku [http://localhost:8080/](http://localhost:8080/). Zobrazí se stránka s jedním citátem a
   obrázkem. Stránka je ovšem statická, při obnově stránky se nic nemění.
1. Uprav stránku tak, aby byla dynamická – aby se při každém načtení text i obrázek náhodně měnil.
1. Zkontroluj výsledek v prohlížeči.
1. *Commitni* a *pushnni* změny (výsledný kód) do svého repository na GitHubu.
1. Vlož odkaz na své repository jako řešení úkolu na portálu [Moje Czechitas](https://moje.czechitas.cz).

## Mohlo by se hodit

Jako zdroj obrázků může použít třeba [Unsplash](https://unsplash.com) – web s obrázky a fotografiemi [zdarma](https://unsplash.com/license). Obrázky z něj můžeš
stáhnout do své aplikace nebo je můžeš odkazovat přímo z jejich webu. Pokud chceš odkázat přímo na fotku s kódem `XXX` (kód je těch cca 10 znaků na konci URL
fotky), můžeš použít následující odkaz:

```
https://source.unsplash.com/XXX
https://source.unsplash.com/XXX/1600x900
```

Druhá varianta určuje požadované rozměry obrázku – pokud má obrázek jiný poměr stran, ořízne se na požadovaný poměr stran. Přesné rozměry obrazovky uživatele
ale neřeš – obrázek se pomocí CSS natáhne nebo smrští tak, aby pokryl celou stránku.

Jako zdroj citátů můžeš použít soubor `src/main/resources/citaty.txt`, který je součástí staženého projektu.

### Náhodná čísla

Pro generování náhodných čísel v Javě slouží třída [Random](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/Random.html).

### Načtení textového souboru z *resourců*

Kód pro načtení řádků souboru v *resourcech* do seznamu řetězců (`List<String>`):

```java
private static List<String> readAllLines(String resource)throws IOException{
    //Soubory z resources se získávají pomocí classloaderu. Nejprve musíme získat aktuální classloader.
    ClassLoader classLoader=Thread.currentThread().getContextClassLoader();

    //Pomocí metody getResourceAsStream() získáme z classloaderu InpuStream, který čte z příslušného souboru.
    //Následně InputStream převedeme na BufferedRead, který čte text v kódování UTF-8 
    try(InputStream inputStream=classLoader.getResourceAsStream(resource);
        BufferedReader reader=new BufferedReader(new InputStreamReader(inputStream,StandardCharsets.UTF_8))){

    //Metoda lines() vrací stream řádků ze souboru. Pomocí kolektoru převedeme Stream<String> na List<String>.
    return reader
        .lines()
        .collect(Collectors.toList());
    }
}

// příklad volání: readAllLines("citaty.txt")
```

### Vytvoření seznamu textových řetězců přímo ve zdrojovém kódu Javy

Pokud chci vytvořit seznam několika textových řetězců a nechci je mít v externím souboru, můžu použít metodu `List.of()`:

```java
List<String> seznamTextu=List.of("řetězec 1","řetězec 2","další řetězec","ještě jiný řetězec");
```

### Obrázek na pozadí v inline stylu

Kaskádové styly (CSS) je možné psát i ve formě *inline stylů* – příslušný CSS kód je uvedený hned u HTML elementu, ke kterému se vztahuje, konkrétně v atributu
`style`. Následující HTML kód tedy vytvoří `div`, který bude mít nastavenou červenou barvu pozadí.

```html

<div style="background-color: red">Tento text má červenou barvu pozadí.</div>
```

### Vložení HTML místo obyčejného textu přes Freemarker

Když se ve Freemarkeru použije interpolace `${text}`, vloží se obsah proměnné `text` do stránky tak, aby bylo v prrohlížeči zobrazeno přesně, to, co je v textu.
Tzn. pokud bude obsahovat nějaké HTML značky, zobrazí se tyto značky na stránce textově, např. `<div>`.
Pokud chceš vložit text jako HTML, je potřeba použít `${text?no_esc}` (tzn. nemá se provádět escapování, tj. nahrazování znaků se speciálním významem).
**Pozor, takto vložený kód se nijak nekontroluje.
Je tedy potřeba takto vkládat pouze HTML kód, kterému důvěřuješ.
V žádném případě takto nelze vkládat kód, který pochází od uživatele.
Uživatel by totiž mohl do kódu podstrčit třeba značku `<script>` a spustit v prohlížeči jakýkoli svůj kód.**

### Odkazy

* odkaz na stránku [Lekce 2](https://java.czechitas.cz/2024-jaro/java-2-online/lekce-2.html)
* Java SE 21 [Javadoc](https://docs.oracle.com/en/java/javase/21/docs/api/java.base/) – dokumentace všech tříd, které jsou součástí základní Javy ve verzi 21.
* Dokumentace [Spring Boot](https://spring.io/projects/spring-boot#learn) – odsud je anotace `@SpringBootApplication` a třída `SpringApplication`.
* Dokumentace [Spring Framework](https://spring.io/projects/spring-framework#learn) – odsud jsou anotace `@Controller`, `@GetRequest` a třída `ModelAndView`.
* Dokumentace [Freemarker](https://freemarker.apache.org/docs/index.html) – šablonovací systém pro HTML použitý v projektu.
* [Unsplash](https://unsplash.com) – obrázky a fotografie k použití zdarma
