[README.md](https://github.com/user-attachments/files/32292376/README.md)
# Torsion Initiation Solver V1 - 2026.09.16

Applicazione web standalone per l'analisi dell'equilibrio torsionale non lineare di un tubo circolare incastrato in **A**, con carichi applicati in **B**.

Il tool risolve l'equazione:

```text
(GJ/L) θ = M_CABLE + W d sin(θ)
```

con la convenzione angolare:

- `θ = 0°`: il peso `W` è sopra il punto `B`;
- `θ = 90°`: il peso è a destra di `B`;
- `θ = 180°`: il peso è sotto `B`.

## Funzionalità

- Input interattivi mediante campi numerici e slider.
- Calcolo automatico del modulo di taglio:

  ```text
  G = E / [2(1 + ν)]
  ```

- Calcolo del momento polare del tubo:

  ```text
  J = π/32 · [OD⁴ − (OD − 2WT)⁴]
  ```

- Ricerca degli equilibri non lineari nell'intervallo `−360° ÷ +360°`.
- Classificazione dell'equilibrio come stabile o instabile.
- Schema statico longitudinale.
- Vista della sezione trasversale in `B` con posizione dinamica del peso.
- Grafico del momento torcente lungo `A–B`.
- Grafico dell'angolo di torsione lungo `A–B`.
- Grafico **Momenti vs θ** con:
  - `M_tube = (GJ/L) θ`;
  - `M_ext = M_CABLE + W d sin(θ)`;
  - punti di equilibrio stabili e instabili.

## KPI visualizzati

- Rotazione A
- Rotazione B
- Torque Moment A
- Torque Moment B
- G
- GJ/L
- lambda
- Equilibrio

Tutti i valori sono arrotondati all'unità, eccetto `lambda`, visualizzato con quattro cifre decimali.

## Utilizzo locale

Non sono richieste dipendenze, installazioni o connessioni Internet.

1. Scaricare il repository.
2. Aprire `index.html` con un browser moderno.
3. Modificare gli input per aggiornare automaticamente risultati, sketch e grafici.

## Pubblicazione con GitHub Pages

1. Caricare `index.html` e `README.md` nella cartella principale del repository.
2. Aprire **Settings** nel repository GitHub.
3. Selezionare **Pages**.
4. In **Build and deployment**, scegliere **Deploy from a branch**.
5. Selezionare il branch `main` e la cartella `/(root)`.
6. Salvare e attendere la pubblicazione del sito.

## Struttura del repository

```text
.
├── index.html
└── README.md
```

## Parametri di input

| Parametro | Descrizione | Unità |
|---|---|---|
| `OD` | Diametro esterno del tubo | mm |
| `WT` | Spessore del tubo | mm |
| `L` | Lunghezza del tubo | m |
| `E` | Modulo di Young | GPa |
| `ν` | Coefficiente di Poisson | – |
| `W` | Peso applicato | kN |
| `d` | Eccentricità del peso rispetto a B | m |
| `M_CABLE` | Momento esterno applicato in B | kN·m |

## Modello e ipotesi

Il modello assume:

- tubo circolare prismatico;
- materiale isotropo elastico lineare;
- torsione di Saint-Venant;
- incastro perfetto in `A`;
- carichi concentrati in `B`;
- comportamento statico;
- angoli espressi in radianti nelle equazioni interne.

Il criterio locale di stabilità è:

```text
Δs = GJ/L − W d cos(θB)
```

- `Δs > 0`: equilibrio stabile;
- `Δs < 0`: equilibrio instabile.

## Compatibilità

Il file è progettato per funzionare nei browser moderni, tra cui:

- Microsoft Edge
- Google Chrome
- Mozilla Firefox
- Safari

## Note

Il tool è destinato a valutazioni ingegneristiche preliminari. I risultati devono essere verificati prima dell'impiego in analisi di progetto o documentazione ufficiale.
