# Efficient Frontier - Analisi portafogli 

**Breve descrizione**

Questo repository contiene un Jupyter Notebook (`EfficientFrontier.ipynb`) che implementa un progetto di analisi di portafoglio in Python: download dei prezzi con `yfinance`, calcolo dei rendimenti, simulazione Monte Carlo di portafogli casuali, calcolo della frontiera efficiente (Markowitz) e visualizzazioni (scatter risk/return, heatmap di correlazione, frontiera).

---

## Cosa c'è in questo repository

* `EfficientFrontier.ipynb` — notebook principale (scarica dati, calcola statistiche, genera portafogli e plot)
* `requirements.txt` — elenco delle librerie Python necessarie
* `README.md` 

---

## Obiettivo del notebook

1. **Scarico dati**: uso `yfinance` per scaricare i prezzi storici per i tickers scelti.
2. **Pulizia & rendimenti**: calcolo rendimenti giornalieri con `pct_change()` e rimuovo i NaN; calcolo media dei rendimenti giornalieri e li annualizzo per ottenere una stima dei rendimenti attesi.
3. **Covarianza**: calcolo la matrice di covarianza dei rendimenti e la annualizzo. È la base per calcolare la varianza del portafoglio
4. **Generazione portafogli (Monte Carlo)**: genero 1000 set di pesi casuali (normalizzati in modo che sommino a 1), per ciascuno calcolo:

   * rendimento atteso del portafoglio: $\mu_p = w^T \mu$
   * volatilità del portafoglio: $\sigma_p = \sqrt{w^T \Sigma w}$
   * Sharpe ratio (opzionale) = ($\mu_p - r_f) / \sigma_p$ (per semplicità si può mettere `r_f = 0`) // da aggiungere 
5. **Visualizzazioni**: scatter risk vs return (nuvola di portafogli), evidenziazione del portafoglio a varianza minima e del portafoglio a Sharpe massimo; heatmap di correlazione.
6. **Output**: notebook produce grafici e un DataFrame riepilogativo (`Return`, `Volatility`, `Sharpe`, colonne `w_<TICKER>` per i pesi) pronto per essere salvato o esportato.

---

## Contenuto di `requirements.txt`

Nel file `requirements.txt` ho inserito le librerie minime necessarie al notebook.

```
yfinance
pandas
numpy
matplotlib
random

```
---


