# Czy sieć z Fashion-MNIST rozpozna moją szafę?

Projekt zaliczeniowy z przedmiotu **Uczenie głębokie** (VIZJA Warszawa, 2026).
Autor: Adam Unrath, nr albumu 53840.

## Cel

Sprawdzić, jak sieć neuronowa wytrenowana na zbiorze [Fashion-MNIST](https://github.com/zalandoresearch/fashion-mnist) radzi sobie z **moimi własnymi zdjęciami ubrań** i dlaczego (nie) radzi sobie dobrze.

Zdjęcia z telefonu nie wyglądają jak dane uczące: inne tło, oświetlenie, kadr i rozdzielczość. Wynik zależy więc w dużej mierze od tego, jak przygotuję dane.

## Pytania badawcze

1. Jak model z laboratorium (MLP) radzi sobie na moich zdjęciach w porównaniu z oficjalnym zbiorem testowym?
2. Czy sieć konwolucyjna (CNN) lepiej znosi różnicę między danymi uczącymi a moimi zdjęciami?
3. Czy augmentacja danych (obrót, przesunięcie, zoom, jasność) zmniejsza tę różnicę?
4. Które klasy są mylone najczęściej i z czego to wynika?

## Dane

| Zbiór | Opis |
|---|---|
| Fashion-MNIST | 70 000 obrazów 28×28 w skali szarości, 10 klas. Pobierany automatycznie przez Keras. |
| Moje zdjęcia | Własne zdjęcia ubrań i dodatków, zapisane w `data/moje_zdjecia/<klasa>/`. |

Przygotowanie zdjęć tak, jak wyglądają dane uczące:

- skala szarości,
- kadr kwadratowy, rozmiar 28×28,
- jasny przedmiot na ciemnym tle (odwrócenie tła, jeśli trzeba),
- wartości pikseli ÷ 255.

## Eksperymenty

Zmieniam **jeden czynnik naraz**, a model wybieram na walidacji. Zbiór końcowy oceniam raz.

| # | Model | Co się zmienia | Trafność (walidacja) | Trafność (moje zdjęcia) |
|---|---|---|---|---|
| 1 | MLP (baseline z laboratorium) | – | _do uzupełnienia_ | _do uzupełnienia_ |
| 2 | CNN | architektura | _do uzupełnienia_ | _do uzupełnienia_ |
| 3 | CNN + augmentacja | dane treningowe | _do uzupełnienia_ | _do uzupełnienia_ |

Wnioski i analiza błędnych predykcji są w notebooku `notebooks/projekt.ipynb`.

## Jak uruchomić

**Google Colab:** otwórz `notebooks/projekt.ipynb` (Plik → Prześlij notatnik lub Otwórz z GitHuba) i uruchamiaj komórki od góry.

**Lokalnie:**

```bash
git clone https://github.com/<twoj-login>/fashion-mnist-moja-szafa.git
cd fashion-mnist-moja-szafa
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter lab
```

## Struktura repozytorium

```
fashion-mnist-moja-szafa/
├── README.md
├── requirements.txt
├── notebooks/
│   └── projekt.ipynb      notebook projektu (szkielet)
├── data/
│   └── moje_zdjecia/      własne zdjęcia, podfolder na klasę
└── wyniki/                tabele eksperymentów, wykresy, zapisane modele
```

## Środowisko

Python 3, TensorFlow/Keras, NumPy, pandas, Matplotlib, Pillow. Szczegóły w `requirements.txt`.
Ziarno losowania jest ustawione w notebooku, ale wyniki mogą się różnić między sprzętem i wersjami bibliotek.

## Źródła

- Materiały z wykładu „Uczenie głębokie” (P. Chomicz, VIZJA), w tym temat „Przygotowanie danych do uczenia głębokiego”.
- Laboratorium: pierwsza sieć neuronowa w Pythonie, Fashion-MNIST.
- Zbiór danych: [Fashion-MNIST](https://github.com/zalandoresearch/fashion-mnist) (Zalando Research).

## Status

Projekt w trakcie. Wyniki i wnioski zostaną uzupełnione po wykonaniu eksperymentów.
