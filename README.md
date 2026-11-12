# Mein Strickjahr 2026 · #oonique2026myknits

Kartengenerator für die OONIQUE-Verlosung im Knitplace. Eine einzige Datei (`index.html`), ohne Build, ohne Server, ohne Tracking. Schriften und Logos sind eingebettet.

## Was die Seite kann

- Deutsch und Englisch, Umschalter oben rechts. Automatisch nach Browsersprache, erzwingbar mit `?lang=de` oder `?lang=en`.
- Kennzahlen: FOs, WIPs, UFOs, Testknits, dazu optional Knäuel und Geribbelt (bei 0 nicht auf der Karte).
- Strick-Typ, der sich aus den Zahlen ergibt (z. B. „UFO-Flotte“, „WIP-Jonglage“), oder frei wählbar.
- Schriftgröße per Regler von 70 bis 140 %. Beim Vergrößern rücken die Abstände zusammen; wo kein Platz mehr ist, sagt die Seite das.
- Lieblingsdesigner:in taggen: bis zu drei Instagram-Handles, erscheinen als „Design: @…“ auf der Karte und als @-Markierung in der Caption.
- Drei Formate: Story 9:16, Beitrag 4:5, transparenter Sticker.
- Teilen am Handy über das System-Teilen-Menü (Instagram erscheint dort als Ziel). Die Caption liegt dabei schon in der Zwischenablage.
- Hashtag `#oonique2026myknits` steht auf der Karte, in der Caption und als Kopier-Knopf auf der Seite.
- Eingaben bleiben im Browser der Nutzer:in gespeichert (localStorage), es wird nichts übertragen.

## Auf GitHub Pages veröffentlichen

1. Neues Repository anlegen, z. B. `oonique2026myknits`, und `index.html` plus `README.md` hochladen.
2. Im Repository: **Settings → Pages → Build and deployment → Source: Deploy from a branch**, Branch `main`, Ordner `/ (root)`, speichern.
3. Nach ein bis zwei Minuten ist die Seite unter `https://bohamuc.github.io/oonique2026myknits/` erreichbar.
4. Optional eigene Domain (z. B. `strickjahr.oonique.com`) unter **Settings → Pages → Custom domain** eintragen und beim DNS-Anbieter einen CNAME auf `bohamuc.github.io` setzen.

## Im Knitplace einbetten

```html
<iframe
  id="oonique-myknits"
  src="https://bohamuc.github.io/oonique2026myknits/?embed=1"
  title="Mein Strickjahr 2026"
  style="width:100%;border:0;min-height:900px"
  allow="web-share; clipboard-write"
  loading="lazy"></iframe>
<script>
  // iframe wächst mit dem Inhalt mit
  window.addEventListener("message", function (e) {
    if (e.data && e.data.type === "oonique2026myknits:height") {
      document.getElementById("oonique-myknits").style.height = e.data.height + "px";
    }
  });
</script>
```

Wichtig ist `allow="web-share; clipboard-write"`. Ohne dieses Attribut darf die eingebettete Seite weder das Teilen-Menü öffnen noch die Caption kopieren; sie fällt dann auf „Bild speichern“ zurück.

Eingebettet blendet die Seite ihr eigenes Logo aus und hat einen transparenten Hintergrund.

Läuft Knitplace als App mit eingebauter Web-Ansicht, ist Teilen und Herunterladen dort oft gesperrt. Die Seite erkennt das, zeigt das fertige Bild zum Lang-Tippen an und empfiehlt, den Link in Safari oder Chrome zu öffnen. Das bitte vor dem Start einmal auf iPhone und Android testen.

## URL-Parameter

| Parameter | Wirkung |
|---|---|
| `?lang=de` / `?lang=en` | Sprache festlegen |
| `?embed=1` | Einbettungs-Ansicht erzwingen (in einem iframe passiert das automatisch) |
| `?share=https://…` | Link, den „Strickfreund:in herausfordern“ verschickt |

## Anpassen

Ganz oben im `<script>` steht der Block `CONFIG`:

```js
const CONFIG = {
  hashtag: "#oonique2026myknits",
  handle: "@oonique",
  year: 2026,
  shareUrl: "",   // z. B. die Knitplace-Seite mit dem Embed
  termsUrl: ""    // Link zu den Teilnahmebedingungen
};
```

Alle Texte beider Sprachen stehen direkt darunter in `I18N`.

## Vor dem Start klären

- Teilnahmebedingungen und Auslosungsdatum (Link in `termsUrl` eintragen, dann erscheint er im Footer).
- `shareUrl` auf die Knitplace-Seite setzen, damit Empfehlungen dort landen und nicht auf der GitHub-Adresse.
- Hashtags in Stories sind nicht durchsuchbar und Stories verschwinden nach 24 Stunden. Story-Teilnahmen findet ihr nur über die `@oonique`-Markierung, Beiträge und Reels über den Hashtag.
