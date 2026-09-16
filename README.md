# Animus Trophy Log

Odškrtávací seznam trofejí z Assassin's Creed na PS5. Jedna HTML stránka, žádný build, žádné závislosti.

**Živá verze:** https://jakub-jen.github.io/ac-trophy-log/

## Co v tom je

| Hra | Trofejí | Na platinu |
|---|---:|---:|
| Assassin's Creed Shadows (PS5) | 55 | 55 |
| Assassin's Creed Mirage (PS5) | 51 | 51 |
| Assassin's Creed Valhalla (PS5) | 87 | 51 |
| Assassin's Creed Odyssey (PS4 na PS5) | 51 | 51 |
| Assassin's Creed Origins (PS4 na PS5) | 59 | 51 |
| **Celkem** | **303** | |

Prstenec u každé hry počítá postup **k platině**, ne ke 100 %. U žádné z těch her se DLC do platiny nepočítá — u Valhally je to rozdíl 87 proti 51. DLC sekce jsou v seznamu označené zvlášť.

Názvy a popisy jsou přeložené do češtiny. Je to vlastní překlad — Ubisoft trofeje do češtiny
nelokalizuje, takže na PSN je uvidíš anglicky. Originální název proto zůstává pod tím českým:
to je to, co hledáš v guidech a na YouTube. U 144 trofejí je navíc tip, co je pro ni potřeba
udělat; trofeje, které jdou nenávratně minout, jsou označené červeně.

### Zatím chybí

- Claws of Awaji (Shadows) — 11 trofejí
- Legacy of the First Blade a Fate of Atlantis (Odyssey)
- Curse of the Pharaohs (Origins)

## Jak se ukládá postup

Postup se drží v `localStorage`, takže žije v tom prohlížeči, kde odškrtáváš. Na přenos jinam jsou dvě cesty:

- **Sync odkaz** — zabalí celý postup do URL. 303 trofejí je bitová mapa o 38 bajtech, po zakódování 52 znaků. Pošleš si odkaz na mobil, otevřeš, postup naskočí. Pokud už na druhém zařízení něco odškrtnutého máš, stránka se nejdřív zeptá, než to přepíše.
- **Záloha do souboru** — JSON ke stažení a načtení zpátky.

Nic se nikam neposílá, žádný server, žádný účet.

Sync odkaz je svázaný s pořadím trofejí v seznamu. Když přibudou chybějící DLC, `SYNC_V` v `index.html` se zvedne a starší odkazy přestanou platit — stránka to pozná a řekne ti to místo toho, aby načetla nesmysl. Zálohy do souboru drží ID trofejí, takže těm to nevadí.

## Spuštění lokálně

Stačí otevřít `index.html` v prohlížeči. Žádný server není potřeba.

## Úpravy

Všechno je v `index.html`. Seznamy trofejí jsou ve skriptu v poli `GAMES`, jedna trofej je `[stupeň, název, popis]`, kde stupeň
je `P`/`G`/`S`/`B` — to je doslovný přepis oficiálního seznamu, tak ať zůstane. Čeština je vedle
v tabulce `CS`, klíčem je anglický název a hodnotou `[český název, český popis, tip]`. Když název
v `CS` chybí, stránka spadne zpátky na originál. Nové sady přidávej na konec hry, ať nerozhodíš pořadí pro sync odkazy.

Data podle [PowerPyx](https://www.powerpyx.com/), u Shadows ověřená proti [Fextralife](https://assassinscreedshadows.wiki.fextralife.com/Trophy+and+Achievement+Guide).
