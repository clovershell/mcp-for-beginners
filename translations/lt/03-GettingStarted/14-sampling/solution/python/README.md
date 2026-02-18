# Šio pavyzdžio vykdymas

Rekomenduojama įdiegti `uv`, bet tai nėra būtina, žr. [instrukcijas](https://docs.astral.sh/uv/#highlights)

## -0- Sukurkite virtualią aplinką

```bash
python -m venv venv
```

## -1- Aktyvuokite virtualią aplinką

```bash
venv\Scripts\activate
```

## -2- Įdiekite priklausomybes

```bash
pip install "mcp[cli]"
```

## -3- Vykdykite pavyzdį


```bash
mcp run server.py
```

## -4- Išbandykite pavyzdį

Paleiskite serverį su komanda:

Pridėkite tai prie *mcp.json* taip:

```json
```

Paleiskite serverį

Parašykite šią užklausą:

```text
prompt
```

Turėtumėte matyti išvestį panašią į:

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Atsakomybės apribojimas**:
Šis dokumentas buvo išverstas naudojant dirbtinio intelekto vertimo paslaugą [Co-op Translator](https://github.com/Azure/co-op-translator). Nors stengiamės užtikrinti tikslumą, atkreipkite dėmesį, kad automatiniai vertimai gali turėti klaidų ar netikslumų. Originalus dokumentas jo gimtąja kalba turėtų būti laikomas autoritetingu šaltiniu. Esant svarbiai informacijai rekomenduojama naudoti profesionalų vertimą žmogaus. Mes neprisiimame atsakomybės už bet kokius nesusipratimus ar klaidingą interpretaciją, kylančią naudojant šį vertimą.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->