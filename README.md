# Домашнее задание 3

[Ссылка на Colab](https://colab.research.google.com/drive/1kDvaRw7zWF9B_64MGrwN-yKenPVgITMX?usp=sharing)

# Основная часть

| Клеточная линия | Клеточная метка | Ссылка                                                                                                                            | Имя при обработке |
| --------------- | --------------- | --------------------------------------------------------------------------------------------------------------------------------- | ----------------- |
| A549            | H4k20me1        | http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneA549H4k20me1Etoh02AlnRep1.bam   | A549H4k20me1      |
| A549            | H3k09me3        | http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneA549H3k09me3Etoh02AlnRep1.bam   | A549H3k09me3      |
| A549            | H3k09ac         | http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneA549H3k09acEtoh02AlnRep1.bam    | A549H3k09ac       |
| A549            | H3k79me2        | http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneA549H3k79me2Dex100nmAlnRep1.bam | A549H3k79me2      |
| A549            | H3k04me3        | http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneA549H3k04me3Dex100nmAlnRep1.bam | A549H3k04me3      |
| A549            | H3k04me2        | http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneA549H3k04me2Dex100nmAlnRep1.bam | A549H3k04me2      |
| A549            | H3k04me1        | http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneA549H3k04me1Dex100nmAlnRep1.bam | A549H3k04me1      |
| A549            | H3k36me3        | http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneA549H3k36me3Dex100nmAlnRep1.bam | A549H3k36me3      |
| A549            | H3k27me3        | http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneA549H3k27me3Dex100nmAlnRep1.bam  | A549H3k27me3      |
| A549            | H3k27ac         | http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneA549H3k27acDex100nmAlnRep1.bam  | A549H3k27ac       |
| A549            | H2az            | http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneA549H2azDex100nmAlnRep1.bam     | A549H2az          |



# H4k20me1



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
