# ia368dd_selecao_leobavila
**IA368DD - Deep Learning aplicado a sistemas de buscas**

Processo Seletivo (Alunos Especiais)

*   Data de entrega: 22/02/2023
*   Nome: Leonardo Bernardi de Avila
*   RA: l224016

Jupyter Notebook: https://colab.research.google.com/drive/1qptsGaiyNfcC4ifnZ6hK-usbXe-n9Dou#scrollTo=KW2Di_KZTzoj

Arquivos de interesse:

* run.cisi.bm25.txt: Este arquivo contém os 1000 principais documentos relevantes para cada consulta da coleção CISI.
A saída está no formato trec eval para que possamos construir algumas métricas de desempenho sobre ela.
* qrels.cisi.txt: O mapeamento de relevância query_id <-> doc_id foi formatado conforme requerido pelo trec eval e salvo neste arquivo.
* ir_system_results.csv: Este arquivo contém os resultados de nosso sistema de recuperação de informações baseado no BM25 e o mapeamento de relevância em formato csv. O número de hits escolhido foi de 1000 por query.
* Exercicio_Selecao.pdf: relatório sobre o projeto feito.

Resultados gerais do sistema para o Collection CISI, com pré-processamento para manter apenas caracteres alfanuméricos e remover stopwords:
```python
P_1                   	all	0.3947
P_3                   	all	0.3728
P_5                   	all	0.3342
```

**Atualização em 23/02/2023:**

Essa alteração foi realizada depois do prazo, mas surtiram efeitos legais no desempenho:

Os parâmetros k1 e b foram alterados e a lista de stopwords foi atualizada para aquela fornecida pelo pacote nltk:

* k1 = 2.2
* b = 0.9

```python
import nltk
from nltk.corpus import stopwords
nltk.download('stopwords')
print(stopwords.words('english'))

# Alteracao na classe BM25 ficaria da forma:
# Stopwords to ignore
self.stopwords = stopwords.words('english')
```
Tais modificações surtiram bom efeito nas métricas apresentadas anteriormente:
```python
P_1                   	all	0.5395
P_3                   	all	0.4342
P_5                   	all	0.3868
```
