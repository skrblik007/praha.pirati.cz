# Web střední Čechy

Web Pirátů ve středních Čechách. Web je zamýšlen pro celé krajské sdružení - veřejnost, členy i pracovníky. Běží na adrese: http://strednicechy.pirati.cz

Pro psaní článků je třeba umět [markdown](https://daringfireball.net/projects/markdown/). Pro zbylé úpravy html a css framework [Foundation 6](http://foundation.zurb.com/). Také je třeba seznámit se alespoň se základy gitu.

## Jak přispívat?

Používáme technologii [Jekyll](http://jekyllrb.com/), která tvoří web ze statických [šablonovaných (Liquid)](https://shopify.github.io/liquid/) stránek. Díky tomu je vše velmi jednoduché:

- články jsou markdown soubory v adresaři `_posts`, obrázky k nim v `assets/img/posts` s rozměry 600x337
- profily lidí z týmu jsou markdown soubory v adresaři `_people`
- stránky jsou klasické html soubory (mohou být i markdown)

### Lokální test

V adresaři s repozitářem spustíme příkaz:
`jekyll serve --incremental --baseurl '' `
což spustí server s webem a my si ho můžeme prohlédnout.

### Správný commit

Pro upload se používá git. Ten rozděluje "uploady" na commity.

Správný commit vždy:

- zachová funkčnost
- dodává 1 funcionalitu (např. nové menu)
- obsahuje popis z kterého je zřejmé, co mění (např.: *Rewrite main menu from Foundation 5 to Foundation 6*)

### Debug cache

1. Stránku vždy vyzkoušíme [lokálně](#lokálni-test) (tím předejdeme chybám jako špatné cesty)
2. Pokud by stránka lokálně nefungovala dobře, tak smažte `_site` a zkuste to znovu
3. Po nahrání na web stránku vyzkoušíme v anonymním okně prohlížeče
4. Zkusíme dát `ctrl+f5`
5. Správná kompilace i tak může trvat např. 5 minut
6. Poslední možností je zaslat prázdný commit, který by měl vynutit přegenerování stránky:  
    ```
    git commit -m 'rebuild pages' --allow-empty  
    git push
    ```

### Standardizace tagů

Články obsahují tagy podle, kterých se následně řadí do rubrik:

Městské části: `praha-1`, `praha-2`, ..., `praha-10`, ..., `praha-22`, `praha-Běchovice`, ...   
Praha jako celek: `Praha`, `ZHMP`

### Adresařova struktura

 Základní schéma:

```
├── _config.yml       - konfigurační soubor
├── _data             - yaml soubory nahrazující DB
├── _includes         - html snippety (hlavička, patička, ...)
│   ├── footer.html   -- patička stránky
│   ├── header.html   -- hlavička stránky
│   └── head.html     -- meta hlavička stránky
├── _layouts          - kompletní šablony stránek
├── _people           - vlastní kolekce obsahující stránky jednotlivých osob
│   ├── osoba.md    
│   └── ...
├── _posts            - příspěvky pro blog v markdownu
├── _sass             - sass styly (konvertované do css)
├── _site             - vygenerovaná stránka
├── assets            - přílohy (obrázky, pdf etc.)
│   └── img           
├── blog              - složka blog / aktuality
│   └── index.html    
├── css               - styly
│   └── main.scss     -- hlavní styl
├── kontakt           
│   └── index.html    
├── o-nas          
│   └── index.html    
├── program
│   └── index.html    
├── transparence
│   └── index.html
├── zapoj-se
│   └── index.html       
└── index.html        - úvodní stránka
```

## Pokročilé

### Výkon

Základním nástrojem pro měření výkonu kompilace: `jekyll build --profile`

TODO:

- dopsat skript pro kontrolu velikosti obrázků
- lépe sladit javascript
- otestovat provoz na vlastním serveru

### Github pages

- [Seznam pluginu povolených na GH](https://pages.github.com/versions/)
- [Compress plugin](http://rich-knight.com/articles/compressing-html-in-jekyll/)  

### Jekyll

```
  <ul>
  {% for category in site.categories %}
      <li>{{ category[0] }}</li>
  {% endfor %}
  </ul>
```

#### Tags v GH

- [Návod na mindust](http://www.minddust.com/post/tags-and-categories-on-github-pages/)
- [Návod ze stackoveflow](http://stackoverflow.com/questions/1408824/an-easy-way-to-support-tags-in-a-jekyll-blog)
- [Návod ze codinfox](https://codinfox.github.io/dev/2015/03/06/use-tags-and-categories-in-your-jekyll-based-github-pages/)

## Použité technologie

- [Komplexní popis problémů](https://developmentseed.org/blog/2011/09/09/jekyll-github-pages/)
- [CSS / JS frontend Foundation 6](http://foundation.zurb.com/), [dokumentace](http://foundation.zurb.com/sites/docs/)
- [CSS template](http://foundation.zurb.com/templates-previews-sites-f6/news-magazine.html)
- integrace soc. sití
  - [Integrace FB](https://365tipu.wordpress.com/2015/07/04/tip185-co-je-to-open-graph-a-proc-je-potreba-aby-designeri-webu-vedeli-o-co-jde/)
  - [Ladění FB](https://365tipu.wordpress.com/2015/04/13/tip103-co-delat-kdyz-facebook-odmita-vlozit-odkaz-na-web/)
- [Disqus a Google analytics, Twitter light share](http://joshualande.com/jekyll-github-pages-poole)
- [Responsibilita](http://design.google.com/resizer/)
- Font pro loga: M+1p Heavy, vel. 72.

## Instalace Jekyll na čistou Fedora 23
```
sudo dnf install gem rubygems-devel gcc ruby-devel
dnf install rpm-build
sudo gem install jekyll  jekyll-paginate
```
