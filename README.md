Noséquè

Aplicació web estàtica en català de divulgació cultural, lingüística i geogràfica amb estètica artesanal de llibreta d'esbossos i aquarel·la, preparada per publicar-se directament a GitHub Pages.

Estructura del projecte

/
├── index.html          # Estructura HTML, estils CSS artesanals i lògica JavaScript
├── articles.json       # Base de dades en format JSON amb els articles del feed
├── LICENSE             # Llicència MIT del codi font
├── README.md           # Documentació tècnica del repositori
├── logo-noseque.png    # Logotip principal de la capçalera (opcional, té fallback)
├── deco-esquerra.png   # Il·lustració decorativa lateral esquerra (opcional)
├── deco-dreta.png      # Il·lustració decorativa lateral dreta (opcional)
└── avatar-autor.png    # Icona o avatar del peu de pàgina (opcional)


Com funciona el codi

Càrrega de dades (fetch): En carregar-se el DOM, index.html executa la funció asíncrona carregarArticlesJSON() per llegir articles.json.

Ordenació i filtratge: Els articles s'ordenen automàticament de més recent a més antic a partir del camp data (AAAA-MM-DD) i es poden filtrar per categoria (Totes, Llengua, Geografia o Cultura).

Persistència local (localStorage): Les reaccions de «M'ha sorprès!» es desen al navegador de l'usuari sota la clau noseque_reaccions_v2 vinculades a l'id únic de cada article.

Gestió d'errors d'imatge (onerror): Si alguna de les il·lustracions decoratives encara no s'ha pujat al repositori, l'aplicació mostra automàticament un marc de reserva sense trencar el disseny.

Com afegir un article nou

Obre articles.json i afegeix un nou objecte dins de l'array principal respectant aquesta estructura:

{
  "id": "art-identificador-unic",
  "data": "2026-11-25",
  "categoria": "Llengua",
  "titol": "Títol de la curiositat",
  "explicacio": [
    "Primer paràgraf amb la dada o explicació principal.",
    "Segon paràgraf amb el context o detall complementari."
  ]
}


Regles dels camps del JSON

id: Text únic per a cada entrada. Si es repeteix, es compartirà el comptador de reaccions a localStorage.

data: Format estrictament AAAA-MM-DD perquè l'ordenació cronològica funcioni bé.

categoria: Ha de coincidir exactament amb "Llengua", "Geografia" o "Cultura".

explicacio: Array de cadenes de text; cada element es renderitza com un paràgraf <p> independent.

Desplegament a GitHub Pages

Puja tots els fitxers a la branca principal del teu repositori públic a GitHub.

Ves a Settings → Pages.

A Source, selecciona Deploy from a branch, tria la branca main i la carpeta / (root), i fes clic a Save.

Nota tècnica: Per provar el projecte en local abans de pujar-lo, cal obrir-lo mitjançant un servidor HTTP local (per exemple, py -m http.server 8000) i no amb doble clic directe (file://), ja que els navegadors bloquegen les peticions fetch() sobre fitxers locals per política CORS.

Llicència

Aquest projecte es distribueix sota la llicència MIT. Consulta el fitxer LICENSE per a més detalls.
