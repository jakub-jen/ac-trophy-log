# Animus Trophy Log

Odškrtávací seznam trofejí z Assassin's Creed na PS5. Jedna HTML stránka, žádný build, žádné závislosti.

**Živá verze:** https://jakub-jen.github.io/ac-trophy-log/

## Co v tom je

| Hra | Rok | Trofejí | Na platinu |
|---|---:|---:|---:|
| Assassin's Creed Shadows (PS5) | 2025 | 55 | 55 |
| Assassin's Creed Mirage (PS5) | 2023 | 51 | 51 |
| Assassin's Creed Valhalla (PS5) | 2020 | 87 | 51 |
| Assassin's Creed Odyssey | 2018 | 51 | 51 |
| Assassin's Creed Origins | 2017 | 59 | 51 |
| Assassin's Creed Syndicate | 2015 | 57 | 50 |
| Assassin's Creed Unity | 2014 | 58 | 51 |
| Assassin's Creed Rogue Remastered | 2014 | 47 | 47 |
| Assassin's Creed IV: Black Flag | 2013 | 57 | 51 |
| Assassin's Creed III Remastered | 2012 | 55 | 55 |
| Assassin's Creed Revelations | 2011 | 50 | 50 |
| Assassin's Creed Brotherhood | 2010 | 51 | 51 |
| Assassin's Creed II | 2009 | 51 | 51 |
| AC Chronicles: China | 2015 | 18 | bez platiny |
| AC Chronicles: India | 2016 | 18 | bez platiny |
| AC Chronicles: Russia | 2016 | 17 | bez platiny |
| **Celkem** | | **782** | **13 platin** |

Kromě tří posledních dílů jsou to verze pro PS4, které na PS5 běží přes zpětnou kompatibilitu.
Assassin's Creed z roku 2007 v seznamu není — vyšel před zavedením trofejí a žádné nemá.

Hry jsou seřazené chronologicky od nejstaršího dílu. Jednu hru si můžeš připnout tlačítkem
**Připnout** v její hlavičce — vyskočí nad ostatní do sekce „Právě hraju“ a stránka se na ní
příště rovnou otevře. Připnutí se drží stejně jako postup, takže platí i na druhém zařízení.

Prstenec u každé hry počítá postup **k platině**, ne ke 100 %. U žádné z těch her se DLC do platiny nepočítá — u Valhally je to rozdíl 87 proti 51. DLC sekce jsou v seznamu označené zvlášť.

Názvy a popisy jsou přeložené do češtiny. Je to vlastní překlad — Ubisoft trofeje do češtiny
nelokalizuje, takže na PSN je uvidíš anglicky. Originální název proto zůstává pod tím českým:
to je to, co hledáš v guidech a na YouTube. Kliknutím na trofej se rozbalí panel s tipem, co je pro ni potřeba udělat — takový tip má 255
z 782 trofejí. Odškrtává se zvlášť, čtverečkem vlevo, takže čtení tipu nic needškrtne.
Trofeje, které jdou nenávratně minout, mají u názvu červený štítek **missable**.

Ve verzi na claude.ai je v tom panelu navíc tlačítko **Zeptat se Claudea**, které se doptá
přímo na konkrétní trofej. Na GitHub Pages se nezobrazuje — to API existuje jen uvnitř
claude.ai. Odpovědi se drží jen do zavření stránky.

### Co hlídat

Dvě platiny závisí na serverech, které Ubisoft může kdykoli vypnout:

- **Unity** — šest trofejí vyžaduje co-op a servery jsou dlouhodobě nespolehlivé
- **Black Flag** — pět trofejí je z multiplayeru, hráčů je minimum

Verze z The Ezio Collection (AC II, Brotherhood, Revelations) multiplayerové trofeje **nemají**,
takže tamní platiny jsou bezpečné, na rozdíl od původních PS3 verzí.

### Zatím chybí

- Claws of Awaji (Shadows) — 11 trofejí
- Legacy of the First Blade a Fate of Atlantis (Odyssey)
- Curse of the Pharaohs (Origins)
- Liberation Remastered — zdroje se rozcházely, radši nemám než špatně

## Jak se ukládá postup

Postup se drží v `localStorage`, takže žije v tom prohlížeči, kde odškrtáváš. Na přenos jinam jsou dvě cesty:

- **Sync odkaz** — zabalí celý postup do URL. 782 trofejí je bitová mapa o 98 bajtech, po zakódování 132 znaků. Pošleš si odkaz na mobil, otevřeš, postup naskočí. Pokud už na druhém zařízení něco odškrtnutého máš, stránka se nejdřív zeptá, než to přepíše.
- **Záloha do souboru** — JSON ke stažení a načtení zpátky.

Nic se nikam neposílá, žádný server, žádný účet.

Sync odkaz je svázaný s počtem trofejí. Bity se řadí podle `id` hry, ne podle toho, jak jsou hry
zobrazené, takže přeskládání seznamu odkazy nerozbije — ale až přibudou chybějící DLC, `SYNC_V`
v `index.html` se zvedne a starší odkazy přestanou platit. Stránka to pozná a řekne ti to místo
toho, aby načetla nesmysl. Zálohy do souboru drží ID trofejí, takže těm to nevadí.

## Spuštění lokálně

Stačí otevřít `index.html` v prohlížeči. Žádný server není potřeba.

## Úpravy

Všechno je v `index.html`. Seznamy trofejí jsou ve skriptu v poli `GAMES`, jedna trofej je `[stupeň, název, popis]`, kde stupeň
je `P`/`G`/`S`/`B` — to je doslovný přepis oficiálního seznamu, tak ať zůstane. Čeština je vedle
v tabulce `CS`, klíčem je anglický název a hodnotou `[český název, český popis, tip]`. Když název
v `CS` chybí, stránka spadne zpátky na originál. Nové sady přidávej na konec hry, ať nerozhodíš pořadí pro sync odkazy.

Data podle [PowerPyx](https://www.powerpyx.com/), u Shadows ověřená proti [Fextralife](https://assassinscreedshadows.wiki.fextralife.com/Trophy+and+Achievement+Guide).
