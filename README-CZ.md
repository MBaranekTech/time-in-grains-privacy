# Zásady ochrany soukromí na GitHub Pages

Pro Google Play potřebujete veřejnou webovou stránku. Nahrajte připravený soubor `publishing/privacy/privacy-policy.html`. Samotný odkaz na soubor v rozhraní GitHubu není cílový odkaz pro Play Console; použijte adresu GitHub Pages podle kroku 5.

Soubor je anglicky, bez JavaScriptu, sledování, cookies, externích fontů a přihlašování. Obsahuje dodané veřejné údaje: **Martin Baránek**, **martin25baranek93@gmail.com**. Před vydáním aplikace je ještě potřeba ověřit konečný Play build a jeho SDK deklarace.

## 1. Vytvořte veřejný repozitář

Na GitHubu zvolte **New repository**:

- **Repository name:** například `time-in-grains-privacy`.
- **Visibility:** Public.
- Zapněte **Add a README file** a klikněte na **Create repository**.

Můžete použít také svůj existující veřejný repozitář. Není potřeba zveřejňovat zdrojový kód aplikace. Do veřejného repozitáře nevkládejte podpisové klíče, hesla, přístupové tokeny ani soukromá data z telefonu.

## 2. Nahrajte jeden HTML soubor

V repozitáři klikněte na **Add file → Upload files** a nahrajte `privacy-policy.html` přímo do kořenové složky. Potvrďte **Commit changes**.

Pokud v novém rozhraní tlačítko nevidíte, na úvodní stránce repozitáře použijte nabídku pro přidání souboru. Název souboru ponechte přesně `privacy-policy.html`.

## 3. Doplňte své veřejné údaje

V dodaném souboru již jsou vaše jméno a e-mail vyplněné. Stačí je zkontrolovat v patičce stránky. Pokud jsou správně, pokračujte krokem 4. Následující úpravy platí pouze pro nevyplněnou verzi šablony.

Otevřete soubor na GitHubu a klikněte na tužku **Edit**. V celém souboru nahraďte:

- `YOUR_PUBLIC_DEVELOPER_NAME` → veřejné jméno vývojáře z Google Play.
- `YOUR_SUPPORT_EMAIL` → váš veřejný kontaktní e-mail; objevuje se v textu i v odkazu `mailto:`.

Smažte celý odstavec začínající `<p class="draft">` a končící `</p>`. Je to upozornění pro přípravu, nikoli součást finálních zásad. Uložte změny přes **Commit changes**.

Pokud chcete, aby se údaje vložily automaticky i do aplikace, pošlete mi jméno, e-mail a budoucí adresu stránky. V projektu se ukládají do `publishing/publisher.json` a generátor vytvoří shodnou HTML stránku i prostředky pro aplikaci:

```sh
python3 tools/prepare-play-release.py
python3 tools/prepare-play-release.py --check
```

Neupravujte pouze vygenerovaný soubor v projektu, pokud ho budete později generovat znovu; generátor používá `publisher.json` a `publishing/privacy/policy.json`. Ruční úpravu na GitHubu mi pošlete jako finální URL, abych mohl údaje sjednotit s aplikací.

## 4. Zapněte GitHub Pages

V repozitáři otevřete **Settings → Pages**. V části **Build and deployment** nastavte:

- **Source:** Deploy from a branch.
- **Branch:** main.
- **Folder:** / (root).

Klikněte na **Save**. Pokud používáte jinou výchozí větev, vyberte ji místo `main`. Počkejte na dokončení nasazení. Stránka Pages ukáže stav a výslednou adresu; případné chyby najdete v kartě **Actions**.

## 5. Ověřte výslednou stránku

Adresa bude zpravidla:

```text
https://VAS_LOGIN.github.io/time-in-grains-privacy/privacy-policy.html
```

`VAS_LOGIN` nahraďte svým GitHub loginem a název repozitáře případně upravte. Pro existující vlastní doménu použijte adresu zobrazenou v Pages a připojte `/privacy-policy.html` podle umístění souboru.

Otevřete tuto adresu v anonymním okně prohlížeče. Musíte vidět hotovou stránku **Time in Grains — Privacy policy**, nikoli kód, GitHub editor, přihlášení nebo chybu 404. Ověřte své jméno a funkční e-mail. Na stránce nesmí zůstat `YOUR_...` ani upozornění Draft.

## 6. Vložte odkaz do Google Play

V Play Console vyberte Time in Grains, otevřete část **App content / Obsah aplikace → Privacy policy / Zásady ochrany soukromí** a vložte výslednou HTTPS adresu. Přesné umístění položky se může lišit podle rozhraní Console.

Stejnou adresu pošlete pro dokončení nastavení aplikace. Aplikace má místní čitelnou kopii zásad; po doplnění adresy nabídne také otevření veřejné stránky v prohlížeči.

Tím dokončíte zveřejnění zásad. Vydání samotné aplikace pokračuje podepsaným AAB, kontrolou Data safety a licenčním testem volitelných Google Play příspěvků. HTML soubor nenahrazuje tyto kroky.

## Oficiální návody

- [GitHub Pages: nastavení zdroje publikování](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)
- [GitHub Pages: vytvoření stránky](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site)
- [Google Play: zásady pro uživatelská data a privacy policy](https://support.google.com/googleplay/android-developer/answer/10144311)

Postup a požadavky ověřeny 20. listopadu 2026.
