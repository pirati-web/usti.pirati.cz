# Web místního sdružení Pirátů k obecnému použití

Naklonovaný web pirati.cz, upravený [Janem Adamcem](https://praha12.pirati.cz/lide/jan-adamec/) a Patrickem Zandlem pro potřeby místních sdružení. Za pět minut můžete mít vlastní web a už si do něj jen vesele vytváříte obsah. 

## Rozchození webu pokud Githubu vůbec nerozumíte

Tak si přečtěte tento malý úvod. 

Systém je vytvořen tak, aby umožňoval snadné publikování webu zdarma přes Github Pages statickým generátorem Jekyll. O něm prakticky nemusíte vědět, je na pozadí Github Pages a nemusíte se o něm dozvědět do okamžiku, kdy budete chtít editovat vzhled stránek - tehdy se hodí vědět, že je použit [template systém Jekyllu](https://jekyllrb.com/docs/templates/) - a to už je pro první kroky vyšší dívčí.

Jak postupovat ke zprovoznění vlastního webu na základě těchto šablon:

* Stiskěte tlačítko Fork vpravo úplně nahoře (vycházím z předpokladu, že už jste se v Githubu registrovali a máte vytvořený účet - pokud ne, bude to asi něco křičet). "Forknete" si tento web,  neboli se vám překopírují všechny soubory do vaší větve Githubu. Tím jste si vytvořili vlastní Repozitář (Repository) na adrese https://github.com/vašeuživatelskéjméno/vášrepozitář/
* Takto forknutý web je ihned viditelný na adrese http://vašeuživatelskéjméno.github.io/brandys-pirati - tu sice můžete používat, ale není moc hezká, takže ji zlepšíme... 
* přejděte do svého repozitáře (kdybyste nevěděli, výpis repozitářů je vlevo)
* vpravo nahoře je ozubené kolečko a Settings - klikněte
* jeďte dolů, tam je část Github Pages - tam si můžete zadat vlastní doménu, pokud ji máte. HTTPS certifikát výrazně doporučuji, ale hned nepůjde zaškrtnout, jeho vygenerování několik dní pro vlastní doménu trvá, tak se sem časem vrátíte. Source a Theme nechte, jak je (source: master) - pokud nevíte, co děláte.
* tím by to mohlo fungovat, ale nefunguje, musíte si ještě nastavit správně DNS u toho, kdo vám spravuje doménu. Je třeba vyplnit následující nastavení v DNS (důležité jsou znáznamy A a CNAME):

![Editace DNS](/assets/img/dns-subreg.png)

Tohle nastavení je tak, jak vypadá v administraci Subreg, u jiných registrátorů je to stejné. Pokud si chcete pořídit doménu třetího řádu typu něco.pirati.cz, musíte se domluvit s jejím sprácem (nevím, kdo to je). Pozor, po editaci DNS trvá něco jako den, než se všechno zpropaguje a funguje po celém internetu. Že vám za pět minut web neběží na nové doméně, je normální, zkuste to druhý den. Pokud jste nastavili doménu výše v administraci Githubu a správně ji spojili s IP adresami v administraci DNS, bude to fungovat. 

## Konfigurace vzhledu webu pro potřebu sdružení

Pokud byste z tohoto našeho chtěli vyjít pro tvorbu webu svého místního sdružení, změňte následující:

- v souboru `_data/links.yaml` změňte hodnoty proměnných, aby se místo pražských věcí zobrazovaly vaše místní
- obrázek `assets/img/header/background.jpg` změňte na nějaký váš lokální
- v adresáři `_people` odstraňte naše lidi a místo toho založte vlastní
- v adresáři `assets/img/people` dejte fotky vašich lidí. Pokud nemáte fotku, používejte `assets/img/people/ppp.jpg`
- v adresáři `_posts` odstraňte naše blogové příspěvky a dávejte vlastní
- v adresáři `assets/img/posts` odstraňte naše fotky pro blogové příspěvky a dávejte vlastní


## Vypublikování webu z Github Pages

Jestliže jste všechno provedli

Jekyll se dá rozběhat nejen na Linuxu, jak se píše níže, ale docela snadno i na macOS a s trochou úsilí i na Windows 10. Návod je například v readme [Pardubického kraje](https://github.com/pirati-web/pardubicky.pirati.cz).

Níže následuje obsah copypastovaný z centrální verze.
## Lokální spuštění

Instalace na Fedora 25: `dnf install rubygem-jekyll`

Instalace Ubuntu 16.04:

```
sudo apt-get install ruby-dev gcc make libghc-zlib-dev
gem install rubygems-update
gem install jekyll bundler
bundle
```

Repozitář můžeme naklonovat do jakékoliv složky (nemusí být ve `/var/www/`).

`jekyll serve`, což stránku zkompiluje, spustí a ještě je stránka přístupná skrz localhost: `http://127.0.0.1:4000`

Popřípadě můžeme spustit jen: `jekyll build`, což do složky `_site` připraví kompletní web (ten můžeme otevřít z prohlíže pomocí klavesové zkratky `ctrl+o`).

## Struktura

Samotné stránky jsou v markdownu nebo v html (složitější struktura, např. vícesloupců apod)

Kolekce jsou markdown soubory s yaml frontend v přísliušné složce, na webu jsou použity 4:

- posts (články)
- people (lidé)
- program
- teams (týmy)

Některé údaje jsou uvedeny v složce `_data`. Jsou zde ve formátu yaml nebo json.

**CSS** je ve složce `_sass` a je automaticky kompilováno a minifikován do jednoho souboru `main.css`.

**JavaScript** je ve složce `_include/js`. Knihovny jsou linkovány skrze CDN v minifikované podobě. Další JS je v spojen do jednoho scriptu bez minifikace (zatím).

Jekyll má velmi podrobnou [dokumentaci](http://jekyllrb.com/docs/home/). A při vývoji též doporučuji [cheat sheet](http://jekyll.tips/jekyll-cheat-sheet/)
