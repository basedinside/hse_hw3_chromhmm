# Домашнее задание 3

[Ссылка на Colab](https://colab.research.google.com/drive/1kDvaRw7zWF9B_64MGrwN-yKenPVgITMX?usp=sharing)

# Основная часть

*В репозитории присутствуют данные для дух прогонов с 10 и 11 состояниями. Я сделал это для лучшего понимания, ниже задания будут для 10 состояний*

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

# Полученные изображения

|![image](https://user-images.githubusercontent.com/71254839/160299709-16919dea-2a81-4e49-a033-677da8f82185.png)|![image](https://user-images.githubusercontent.com/71254839/160299737-080f0276-625c-438a-909f-451ca4e80bc7.png)|
|---|---|
|![image](https://user-images.githubusercontent.com/71254839/160299746-a89fd997-0bfa-4033-ac22-4b3f83c89e9d.png)|![image](https://user-images.githubusercontent.com/71254839/160299753-4d8eb404-8837-4aa6-9029-5a498bc50f3f.png)|
|![image](https://user-images.githubusercontent.com/71254839/160299759-9befc68d-8e6a-46d3-afc9-3b23271190a4.png)||

# Анализ данных статьи

В статье были выделены следующие группы генов:
- Promotor-assosiated. Ими оказались **60% всех RefSeq TSS**, и ими было покрыто **всего 1.3%** генома. 
- Transcription-assosiated. Они составляют от **70 до 95% RefSeq-annotated transcribed regions**. Отличительной чертой данной группы является то, что она **широко представлена среди ВСЕХ видов отметок**. Чаще всего представлена **комбинацией меток**, а не какой-то одной.
- Active intergenic. В эту группу входят инсуляторы и энхансеры. Зачастую они находятся вдалеке от **промоторов и тарнскрибируемых генов**, могут располагаться на снипах. **При пересечении с генами, эти участки подавляют их экспрессию**.
- Large scale repressed states. Эти регионы подвергаются наибольшей упаковке во время деления клетки и представляют **до 64% генома**.
- Repetetive. В основном представлены повторами **CA, TG, CATG**.

# Изучение материалов домашнего задания

## Промоторы

Начнем с первой группы - промоторов. Нам известно, что они часто встречаются в TSS, поэтому посмотрим, какое состояние часто представлено в TSS. Судя по Fold Enrichment, наиболее подходящие кандидаты - состояния 7,8,9. 

Также стоит учитывать тот факт, что они являются довольно малочисленной группой - всего 1.3%.

![image](https://user-images.githubusercontent.com/71254839/160302576-840ce714-22c1-4dca-a9ce-d86fc1fe1060.png)

По картинке видно, что эти состояния довольно неплохо походят на промоторов. 

Метки, соответствующие промоторам - H3K4m2, H3K4m3, H3k9ac, H3K27ac

## Транскрибируемые участки

Эти состояния широко представлены в генах, от 70 до 95%. Также стоит отметить то, что эти состояния часто представлены комбинацией, а не одним состоянием.

![image](https://user-images.githubusercontent.com/71254839/160303008-b3e36157-d1de-49aa-a302-5221cc3bee5b.png)

Как можно заметить, состояния 4, 5 и 6 часто идут комбинацией, с высокой долей вероятности эти состояния и относятся к транскрибируемым участкам. Эта догадка подтверждается матрицей Fold Enrichment, где состояния 4, 5 и 6 имеют насыщенный синий цвет на пересечении с RefSeqGene, при этом состояние 4 ярко закрашено на пересечении с экзоном.

При взгляде на картинку видно, что 4 действительно часто попадает на экзоны, а 5 и 6 на интроны. Еще можно отметить, что состояние 4 в среднем меньше, чем состояние 5.

Также стоит отметить, что состояние 9 тоже может быть транскирибируемым.

Метки, соответствующие данным состояниям - H3K79m2

## Широко репрессируемые участки

Ожидается, что эти участки будут широко представлены в межгенном пространстве. Для подсказки снова обратимся к матрице. Заметим, что стоит искать состояния 1 и 2.

![image](https://user-images.githubusercontent.com/71254839/160303518-2cd1cf60-9a68-437a-a133-612fa74e93be.png)

Догадки подтверждаются. 

Метки для данных состояний: H3K27m3, H3K9m3

![image](https://user-images.githubusercontent.com/71254839/160303774-1a2d8ddb-a330-4a21-b035-0a417edf6287.png)

## Active intergenic

Я думаю, что стоит искать небольшой длины состояния, которые находятся в далеке от генов.

Лучше всего под это описание подходит состояние 3. Кроме того, мне удалось найти место, в котором это состояние пересекается с геном и сам ген, судя по всему заглушен.

![image](https://user-images.githubusercontent.com/71254839/160303937-19f54d80-ed4d-43e0-8079-0d4bb39b29f6.png)

Для данного состояния подходят метки: H3K9m3, H2az, H4K20m1, H3K27m3

## Repetetive

Отличительной чертой данного состояния является то, что часто представлены пары AT и CG. Возможно сюда подходит состояние 10, потому что больше не смог никуда его отнести. 

![image](https://user-images.githubusercontent.com/71254839/160304293-d4713e85-bda7-4fbf-88a2-84338dccba94.png)

В браузере видно много АС и ТG, так что вполне возможно, что 10 сюда подходит.

Данное состояние представлено метками: H3K4m2, H3K36m3, H3K4m3

# Вывод

| Клеточная метка | Состояния | Подходящая группа    |
| --------------- | --------- | -------------------- |
| H4k20me1        | 3         | Active Intergenic    |
| H3k09me3        | 3         | Active Intergenic    |
| H3k09ac         | 7,8,9     | Promotor             |
| H3k79me2        | 4,5,6     | Transcribe           |
| H3k04me3        | 7,8,9,10  | Promotor, Repetetive |
| H3k04me2        | 7,8,9,10  | Promotor, Repetetive |
| H3k04me1        | -         | -                    |
| H3k36me3        | 10        | Repetetive           |
| H3k27me3        | 3         | Active Intergenic    |
| H3k27ac         | 7,8,9     | Promotor             |
| H2az            | 3         | Active Intergenic    | 

# Бонус

```python
!pip install pybedtools

import pandas as pd
import pybedtools


old = pd.read_csv('/content/data/A549_10_dense.bed', sep=' ', skiprows=1, names=['0', '1', '2', 'state', '3', '4', '5', '6', '7'])
expanded_names=['0', '1_Repressed', '2_Repressed', '3_Active_Intergenic', '4_Intron', '5_Exon', '6_Exon', '7_Inactive/poised_Promoter', '8_Weak_promotor', '9_Active_promotor', '10_Repetetive']

new = old.copy()
new['state'] = new['state'].apply(lambda x: expanded_names[x])
x = pybedtools.BedTool.from_dataframe(new)
x.saveas('x.bed')
```

![image](https://user-images.githubusercontent.com/71254839/160305217-b30431b6-dc03-4aa1-af9f-69793f3568bd.png)


