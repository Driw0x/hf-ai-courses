# Biais et limites
> Source : [Hugging Face LLM Course — Bias and limitations](https://huggingface.co/learn/llm-course/en/chapter1/9)

Lors de l'utilisation d'un modèle pré-entraîné ou une version *fine-tunée*, il faut savoir que ces outils ont leurs limites. Pour permettre le pré-entraînement sur de grandes quantités de données, les chercheurs peuvent récupérer des données incorrectes d'internet.

[Exemple d'un pipeline `fill-mask` avec le modèle BERT](../notebooks/section8.ipynb) :

```python
from transformers import pipeline

unmasker = pipeline("fill-mask", model="bert-base-uncased")
result = unmasker("This man works as a [MASK].")
print([r["token_str"] for r in result])

result = unmasker("This woman works as a [MASK].")
print([r["token_str"] for r in result])
```

```text
['lawyer', 'carpenter', 'doctor', 'waiter', 'mechanic']
['nurse', 'waitress', 'teacher', 'maid', 'prostitute']
```

Le modèle ne donne qu'une seule réponse qui ne soit pas liée à un genre (waiter/waitress). Les autres sont des professions généralement associées à un genre particulier et « prostitute » (prostituée) figure parmi les cinq possibilités les plus probables que le modèle associe à « woman » (femme) et « work » (travail). Cela se produit alors que BERT est l'un des rares modèles Transformer qui n'aient pas été construits en récupérant des données partout sur Internet, mais plutôt en utilisant des données apparemment neutres (il a été entraîné sur les jeux de données [Wikipédia en anglais](https://huggingface.co/datasets/wikipedia) et [BookCorpus](https://huggingface.co/datasets/bookcorpus)).

Le modèle d'origine utilisé pourrait très facilement générer du contenu sexiste, raciste ou homophobe. Le *fine-tuning* du modèle sur d'autres données ne fera pas disparaître ce biais.
