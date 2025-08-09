# KONFIGURACJA USTAWIEŃ SERWERA
<!doctype html>
<html lang="pl">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Dokumentacja — Ustawienia serwera (Properties) • Minecraft</title>
  <meta name="description" content="Czytelna dokumentacja online ustawień serwera Minecraft: opis opcji w panelu Properties, zalecenia konfiguracyjne i linki do źródeł." />
  <style>
    :root{
      --bg:#0b1020; --panel:#141a2e; --muted:#97a3b6; --txt:#e6ecf6; --pri:#4e8cff; --ok:#20c997; --warn:#ffb020; --bad:#ff6b6b; --br:16px;
    }
    *{box-sizing:border-box}
    html,body{margin:0;height:100%;background:var(--bg);color:var(--txt);font:16px/1.6 system-ui,-apple-system,Segoe UI,Roboto,Ubuntu,"Helvetica Neue",Arial}
    a{color:var(--pri);text-decoration:none}
    a:hover{text-decoration:underline}
    .container{max-width:1100px;margin:0 auto;padding:24px}
    header{display:flex;gap:18px;align-items:center;justify-content:space-between;margin-bottom:18px}
    .brand{display:flex;gap:12px;align-items:center}
    .logo{width:40px;height:40px;border-radius:12px;background:linear-gradient(135deg,var(--pri),#8ca8ff)}
    h1{font-size:clamp(22px,2.6vw,34px);margin:0}
    .card{background:var(--panel);border-radius:var(--br);padding:18px;box-shadow:0 10px 30px rgba(0,0,0,.25);border:1px solid rgba(255,255,255,.05)}
    .grid{display:grid;grid-template-columns:1fr;gap:16px}
    @media(min-width:900px){.grid{grid-template-columns:1.1fr .9fr}}
    h2{margin:0 0 10px;font-size:22px}
    h3{margin:18px 0 8px;font-size:18px}
    .muted{color:var(--muted)}
    .kbd{font:600 12px/1.2 ui-monospace,SFMono-Regular,Menlo,Consolas,monospace;padding:2px 6px;border-radius:6px;background:#0f1426;border:1px solid rgba(255,255,255,.06)}
    .toc{display:flex;flex-wrap:wrap;gap:8px}
    .toc a{padding:8px 10px;border-radius:10px;background:#0f1426;border:1px solid rgba(255,255,255,.06)}
    table{width:100%;border-collapse:separate;border-spacing:0}
    th,td{padding:12px 14px;vertical-align:top}
    thead th{position:sticky;top:0;background:#0f1426;border-bottom:1px solid rgba(255,255,255,.12);z-index:1}
    tbody tr{border-bottom:1px solid rgba(255,255,255,.06)}
    tbody tr:hover{background:rgba(255,255,255,.03)}
    .badge{display:inline-flex;align-items:center;gap:6px;padding:4px 8px;border-radius:999px;border:1px solid rgba(255,255,255,.12);font-size:12px}
    .b-ok{background:rgba(32,201,151,.12);border-color:rgba(32,201,151,.35)}
    .b-warn{background:rgba(255,176,32,.12);border-color:rgba(255,176,32,.35)}
    .b-bad{background:rgba(255,107,107,.12);border-color:rgba(255,107,107,.35)}
    .code{background:#0f1426;border:1px solid rgba(255,255,255,.06);border-radius:12px;padding:12px;overflow:auto}
    .footer{margin-top:24px;color:var(--muted);font-size:14px}
    .small{font-size:13px}
  </style>
</head>
<body>
  <div class="container">
    <header>
      <div class="brand">
        <div class="logo" aria-hidden="true"></div>
        <div>
          <h1>Dokumentacja — Ustawienia serwera <span class="muted">(sekcja <em>Properties</em>)</span></h1>
          <div class="small muted">Produkt: Minecraft (silniki: Vanilla / Spigot / Paper / modpacki zgodne z <code>server.properties</code>)</div>
        </div>
      </div>
      <div class="badge">Wersja dokumentu: 1.0</div>
    </header>

    <div class="grid">
      <section class="card">
        <h2>Spis treści</h2>
        <nav class="toc" aria-label="Spis treści">
          <a href="#opis-opcji">Opis opcji</a>
          <a href="#zalecenia">Zalecenia wg typu serwera</a>
          <a href="#faq">FAQ</a>
          <a href="#linki">Linki i źródła</a>
          <a href="#zmiany">Historia zmian</a>
        </nav>
      </section>

      <section class="card">
        <h2>Streszczenie</h2>
        <p>Ta strona dokumentuje kluczowe ustawienia z panelu <strong>Properties</strong> serwera Minecraft. Każda opcja ma opis funkcjonalny, spodziewany wpływ na rozgrywkę oraz typowe wartości. Konfiguracja jest zgodna z konwencją pliku <span class="kbd">server.properties</span> wykorzystywaną przez większość dystrybucji serwerowych.</p>
        <p class="muted small">Uwaga: nazwy w interfejsie panelu mogą różnić się w zależności od hostingu lub nakładki administracyjnej. Poniższe opisy odnoszą się do standardowego zachowania silnika gry.</p>
      </section>
    </div>

    <section id="opis-opcji" class="card" aria-labelledby="h-opis">
      <h2 id="h-opis">Opis opcji</h2>
      <div class="small muted" style="margin-bottom:8px">Kolumny: nazwa w panelu • typ danych • dopuszczalne wartości • opis działania</div>
      <div class="code small" aria-hidden="true">Przykład w pliku server.properties: <br> <code>allow-flight=false</code></div>
      <div style="overflow:auto">
        <table role="table" aria-label="Tabela opcji">
          <thead>
            <tr>
              <th scope="col">Nazwa opcji</th>
              <th scope="col">Typ</th>
              <th scope="col">Wartości</th>
              <th scope="col">Opis działania</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td><strong>Accepts Transfers</strong></td>
              <td>Boolean</td>
              <td><span class="kbd">Enabled</span> / <span class="kbd">Disabled</span></td>
              <td>Pozwala przyjmować graczy przenoszonych z innych serwerów (proxy: BungeeCord/Velocity). <em>Disabled</em> — blokuje takie połączenia.
              </td>
            </tr>
            <tr>
              <td><strong>Allow Flight</strong></td>
              <td>Boolean</td>
              <td><span class="kbd">Enabled</span> / <span class="kbd">Disabled</span></td>
              <td>Umożliwia latanie w trybie Survival bez automatycznego wyrzucenia za podejrzenie cheatów. Przy <em>Disabled</em> gracze mogą być wyrzucani podczas lotu (z wyjątkiem legalnych mechanik, np. elytra).</td>
            </tr>
            <tr>
              <td><strong>Allow Nether</strong></td>
              <td>Boolean</td>
              <td><span class="kbd">Enabled</span> / <span class="kbd">Disabled</span></td>
              <td>Włącza/wyłącza świat Nether. <em>Disabled</em> — portale nie działają.</td>
            </tr>
            <tr>
              <td><strong>Broadcast Console To Ops</strong></td>
              <td>Boolean</td>
              <td><span class="kbd">Enabled</span> / <span class="kbd">Disabled</span></td>
              <td>Wysyła komunikaty z konsoli serwera na czat graczy z rangą OP. Może powodować „szum” informacyjny przy wielu pluginach.</td>
            </tr>
            <tr>
              <td><strong>Broadcast RCON To Ops</strong></td>
              <td>Boolean</td>
              <td><span class="kbd">Enabled</span> / <span class="kbd">Disabled</span></td>
              <td>Pokazuje na czacie OP polecenia uruchamiane przez RCON (zdalne zarządzanie). Przy serwerach publicznych często <em>Disabled</em> ze względów czytelności.</td>
            </tr>
            <tr>
              <td><strong>Bug Report Link</strong></td>
              <td>URL (tekst)</td>
              <td>np. <span class="kbd">https://twoj-serwer.example/bug</span></td>
              <td>Adres do zgłaszania błędów (formularz, Discord, GitHub Issues). Puste — brak centralnego kanału zgłoszeń.</td>
            </tr>
            <tr>
              <td><strong>Difficulty</strong></td>
              <td>Enum</td>
              <td><span class="kbd">Peaceful</span>, <span class="kbd">Easy</span>, <span class="kbd">Normal</span>, <span class="kbd">Hard</span></td>
              <td>Poziom trudności: wpływa na generowanie i siłę mobów, głód, obrażenia i regenerację.</td>
            </tr>
          </tbody>
        </table>
      </div>
    </section>

    <section id="zalecenia" class="card" aria-labelledby="h-zalecenia">
      <h2 id="h-zalecenia">Zalecenia wg typu serwera</h2>
      <div class="grid" style="grid-template-columns:repeat(auto-fit,minmax(260px,1fr));gap:12px">
        <div class="card" style="padding:14px">
          <h3>Survival</h3>
          <ul>
            <li><span class="badge b-warn">Allow Flight: Disabled</span> — antycheat ma mniej fałszywych alarmów.</li>
            <li><span class="badge b-ok">Allow Nether: Enabled</span> — pełna eksploracja.</li>
            <li><span class="badge b-ok">Difficulty: Normal/Hard</span> — większe wyzwanie.</li>
          </ul>
        </div>
        <div class="card" style="padding:14px">
          <h3>Creative / Build</h3>
          <ul>
            <li><span class="badge b-ok">Allow Flight: Enabled</span> — swobodne latanie.</li>
            <li><span class="badge">Allow Nether: opcjonalnie Disabled</span> — mniej światów do utrzymania.</li>
            <li><span class="badge">Difficulty: Peaceful</span> — brak mobów i głodu.</li>
          </ul>
        </div>
        <div class="card" style="padding:14px">
          <h3>Event / Mini‑gry</h3>
          <ul>
            <li><span class="badge">Allow Nether: zależnie od mapy</span></li>
            <li><span class="badge">Allow Flight: wg mechanik</span></li>
            <li><span class="badge b-warn">Broadcast Console/RCON: zwykle Disabled</span> — mniej spamu.</li>
          </ul>
        </div>
      </div>
    </section>

    <section id="faq" class="card" aria-labelledby="h-faq">
      <h2 id="h-faq">FAQ</h2>
      <h3>Czy <em>Allow Flight</em> jest wymagane dla Elytry?</h3>
      <p>Nie — Elytra to legalna mechanika. Jednak niektóre antycheaty mogą wymagać wyjątków; testuj na swoim zestawie pluginów.</p>
      <h3>Co daje <em>Accepts Transfers</em> na serwerze solo?</h3>
      <p>Na serwerze bez proxy zwykle pozostaje <em>Disabled</em>. W sieciach wielu serwerów ustaw <em>Enabled</em> dla poprawnych transferów graczy.</p>
      <h3>Czy wyłączenie <em>Broadcast Console to Ops</em> ukryje błędy pluginów?</h3>
      <p>Wiadomości nie znikają — nadal są w konsoli/logach. Opcja steruje tylko tym, co widzą operatorzy w grze.</p>
    </section>

    <section id="linki" class="card" aria-labelledby="h-linki">
      <h2 id="h-linki">Linki i źródła</h2>
      <ul>
        <li><a href="https://minecraft.fandom.com/wiki/Server.properties" target="_blank" rel="noopener">Oficjalne pola pliku <code>server.properties</code> — Fandom Wiki</a></li>
        <li><a href="https://wiki.vg/RCON" target="_blank" rel="noopener">RCON — opis protokołu (wiki.vg)</a></li>
        <li><a href="https://www.spigotmc.org/wiki/bungeecord/" target="_blank" rel="noopener">BungeeCord — dokumentacja (Spigot)</a></li>
      </ul>
    </section>

    <section id="zmiany" class="card" aria-labelledby="h-zmiany">
      <h2 id="h-zmiany">Historia zmian</h2>
      <ul class="small">
        <li><strong>1.0</strong> — pierwsza wersja: opis opcji z panelu, rekomendacje, FAQ i źródła.</li>
      </ul>
    </section>

    <footer class="footer">
      Przygotowano do publikacji online (wiki / GitHub Pages). Możesz skopiować ten plik jako <span class="kbd">properties-doc.html</span> i hostować statycznie.
    </footer>
  </div>
</body>
</html>
