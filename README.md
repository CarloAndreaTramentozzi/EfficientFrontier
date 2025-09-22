# Efficient Frontier — Analisi portafogli (Notebook)

**Breve descrizione**

Questo repository contiene un Jupyter Notebook (`EfficientFrontier.ipynb`) che implementa un progetto di analisi di portafoglio in Python: download dei prezzi con `yfinance`, calcolo dei rendimenti, simulazione Monte Carlo di portafogli casuali, calcolo della frontiera efficiente (Markowitz) e visualizzazioni (scatter risk/return, heatmap di correlazione, frontiera).

---

## Cosa c'è in questo repository

* `EfficientFrontier.ipynb` — notebook principale (scarica dati, calcola statistiche, genera portafogli e plot)
* `requirements.txt` — elenco delle librerie Python necessarie
* `README.md` 

---

## Obiettivo del notebook

1. **Scarico dati**: uso `yfinance` per scaricare i prezzi storici per tickers scelti.
2. **Pulizia & rendimenti**: calcolo rendimenti giornalieri con `pct_change()` e rimuovo i NaN; calcolo media dei rendimenti giornalieri e li annualizzo per ottenere una stima dei rendimenti attesi.
3. **Covarianza**: calcolo la matrice di covarianza dei rendimenti e la annualizzo. È la base per calcolare la varianza del portafoglio
4. **Generazione portafogli (Monte Carlo)**: genero 1000 set di pesi casuali (normalizzati in modo che sommino a 1), per ciascuno calcolo:

   * rendimento atteso del portafoglio: $\mu_p = w^T \mu$
   * volatilità del portafoglio: $\sigma_p = \sqrt{w^T \Sigma w}$
   * Sharpe ratio (opzionale) = ($\mu_p - r_f) / \sigma_p$ (per semplicità si può mettere `r_f = 0`)
5. **Visualizzazioni**: scatter risk vs return (nuvola di portafogli), evidenziazione del portafoglio a varianza minima e del portafoglio a Sharpe massimo; heatmap di correlazione.
6. **Output**: notebook produce grafici e un DataFrame riepilogativo (`Return`, `Volatility`, `Sharpe`, colonne `w_<TICKER>` per i pesi) pronto per essere salvato o esportato.

---

## Come eseguire (ambiente consigliato)

1. **Creare un virtual environment** (consigliato):

```bash
python -m venv env
# Linux / macOS
source env/bin/activate
# Windows (PowerShell)
env\Scripts\Activate.ps1
```

2. **Installare dipendenze**

```bash
pip install -r requirements.txt
```

3. **Lanciare Jupyter**

```bash
jupyter notebook
# oppure
jupyter lab
```

4. Aprire `EfficientFrontier.ipynb` ed eseguire le celle in ordine. Il notebook contiene commenti e celle di setup già pronte.

---

## Contenuto di `requirements.txt`

Nel file `requirements.txt` ho inserito le librerie minime necessarie al notebook. Se vuoi, puoi aggiungere version pin specifiche.

```
yfinance
pandas
numpy
matplotlib
seaborn
scipy
jupyter
```

(Opzionali/complementari)

```
streamlit   # se vuoi creare una dashboard interattiva
notebook
jupyterlab
```

---

## Suggerimento per `.gitignore`

È buona pratica escludere file voluminosi, file temporanei e ambienti virtuali dal repository. Esempio di `.gitignore` da includere:

```
# Python
__pycache__/
*.py[cod]
*.so

# Environments
env/
.venv/

# Jupyter
.ipynb_checkpoints/

# Data
/data/
*.csv

# OS files
.DS_Store
Thumbs.db

# IDE
.vscode/
.idea/
```

> Nota: se vuoi committare un piccolo CSV di esempio (es. `data/sample.csv`) per permettere a chi clona il repo di eseguire il notebook senza scaricare i dati via Internet, non includere `data/` in `.gitignore` oppure aggiungi un file `data/.gitkeep` e committa solo quello.

---

## Suggerimenti su cosa mettere nel README per i recruiter

* Spiega brevemente lo scopo del progetto e il tuo ruolo (es. “implementazione personale dell’Efficient Frontier in Python, con spiegazione teorica e visualizzazioni”).
* Inserisci uno screenshot dei grafici principali (nuvola risk/return, heatmap correlazioni, punto min varianza).
* Metti una sezione “Risultati principali” con 2-3 osservazioni ricavate dall’analisi.
* Aggiungi una sezione “Next steps” (es. aggiungere vincoli, implementare ottimizzazione convessa con `scipy.optimize`, backtest su rolling windows, usare fattori, portafoglio ottimizzato con rischio target, ecc.).

---

## Come aggiungere i file su GitHub (rapido)

```bash
git init
git add EfficientFrontier.ipynb README.md requirements.txt .gitignore
git commit -m "Initial commit: Efficient Frontier notebook + README"
# creare repo su GitHub e poi:
git remote add origin <url_repo>
git push -u origin master
```

---

## Licenza & Credits

Se vuoi rendere il repository pubblico considera di aggiungere una licenza (es. MIT). Se hai preso codice o idee da terzi, aggiungi i riferimenti.

---

## Vuoi che modifichi qualcosa?

Se vuoi posso:

* tradurre il README in inglese
* aggiungere badge (Python, build, license)
* generare un file `requirements.txt` con version pin (es. `numpy>=1.24.0`)
* creare una versione `README_short.md` da usare come descrizione del repo

Dimmi cosa preferisci e lo aggiorno.
