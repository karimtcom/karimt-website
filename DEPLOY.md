# karimt.com. Live zetten en beheren

Dit pakket is de afgewerkte website van karimt.com, klaar om te deployen. Zelfde stack als
rt107mm.be en untold-legacy.com, maar zonder CMS: GitHub (code) plus Netlify (hosting) plus
je registrar voor de DNS.

De zware Claude Design bundel is uitgepakt naar een schone statische site. Geen React-runtime
meer, geen design-canvas. Teksten staan vast in index.html, beelden en fonts in assets.

## Wat zit erin

```
karimt-site/
├── index.html        de volledige website (een pagina, alle secties)
├── assets/           portret, klantlogo's, KT-logo en webfonts
├── netlify.toml      zet de build uit zodat Netlify niets fout autodetecteert
├── robots.txt
└── DEPLOY.md         dit bestand
```

## Twee dingen om vooraf te beslissen

1. Adres. De site toont nu Rozenstraat 5/004, dat is je thuisadres. Beslis of dat publiek mag
   staan, of dat we er Dorpsstraat 25B (karimt.com HQ) van maken. Ik pas het in een lijn aan,
   zeg het maar voor je live gaat.
2. Taal. De site staat op Engels. De Nederlandse versie zit volledig klaar in de code maar is
   uitgeschakeld. Later aanzetten of tweetalig maken kan altijd.

Account: dit is jouw merk, dus gewoon je eigen GitHub en Netlify. Geen clubaccount nodig zoals
bij Ronde Tafel.

## Stap 1. Code op GitHub

1. Maak een nieuwe repository, bijvoorbeeld `karimt-website`. Private mag, public mag.
2. Upload de volledige inhoud van deze map via de GitHub-website: "Add file, Upload files",
   sleep index.html, de map assets, netlify.toml en robots.txt erin. Commit naar de branch `main`.
3. Behoud de mapstructuur. assets moet als map in de repo staan, niet als losse bestanden.

## Stap 2. Hosting op Netlify

1. Log in op netlify.com, de gratis tier volstaat ruim.
2. "Add new site, Import an existing project", koppel GitHub en kies je repo.
3. Build settings: build command leeg laten, publish directory op `.`. De netlify.toml regelt dit
   al, dus laat staan wat er staat.
4. Deploy. Je krijgt een tijdelijke URL zoals `random-naam.netlify.app`.
5. Open die URL en scroll de hele site door. Alles hoort te staan: header met logo, hero met je
   portret en de KT-tekening, de zeven domeinen, de logomarquee, de donkere testimonialbalk,
   contact en de footer met de volledige lockup.

Test dit grondig op de tijdelijke URL voor je de DNS aanpast. Zo is de overschakeling naadloos.

## Stap 3. karimt.com koppelen

Let op: karimt.com wijst nu nog naar je oude Webnode-site. Doe deze stap pas als de Netlify-URL
goed is getest.

1. In Netlify: "Domain settings, Add a domain", vul `karimt.com` in en voeg ook `www.karimt.com` toe.
2. Netlify toont welke DNS-records je moet instellen. Ga naar de plek waar karimt.com nu beheerd
   wordt (je huidige registrar of hostingprovider) en kies een van twee:
   - Eenvoudigst: zet de nameservers van het domein naar die van Netlify. Netlify beheert dan alles.
   - Of: voeg bij je registrar de records toe die Netlify toont, doorgaans een A-record voor het
     kale domein en een CNAME voor www naar je-site.netlify.app.
3. Netlify regelt automatisch een gratis HTTPS-certificaat. DNS kan tot 24 uur duren, meestal sneller.

## Stap 4. Oude site opzeggen

Zodra karimt.com correct op Netlify draait met HTTPS, mag je de oude Webnode-site afsluiten.
Behoud de domeinnaam zelf, alleen de hosting bij Webnode mag weg.

## Later iets wijzigen

Geen CMS, dus tekst of beeld aanpassen doe je in de repo. Tekst staat in index.html, beelden in
assets. Wijzig het bestand, commit naar main, en Netlify herpubliceert vanzelf binnen een minuut.
Als je liever niet zelf in de code zit, stuur je mij de wijziging en lever ik een nieuwe index.html.
