# Домашнее задание 3

[Ссылка на Colab](https://colab.research.google.com/drive/1kDvaRw7zWF9B_64MGrwN-yKenPVgITMX?usp=sharing)

# Основная часть



# Бонус

```python
!pip install pybedtools

import pandas as pd
import pybedtools


old = pd.read_csv('/content/data/A549_10_dense.bed', sep=' ', skiprows=1, names=['0', '1', '2', 'state', '3', '4', '5', '6', '7'])
expanded_names=['0', '1_Active_Promoter', '2_Weak_Promoter', '3_Inactive/poised_Promoter', '4_Strong_enhancer', '5_Strong_enhancer', '6_Weak/poised_enhancer', '7_Weak/poised_enhancer', '8_Insulator', '9_Transcriptional_transition', '10_Transcriptional_elongation']

new = old.copy()
new['state'] = new['state'].apply(lambda x: expanded_names[x])
x = pybedtools.BedTool.from_dataframe(new)
x.saveas('x.bed')
```

![image](https://user-images.githubusercontent.com/71254839/160294770-687ed9ad-5c05-4977-bdfc-a1963db10fee.png)
