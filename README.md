# EDUsum-dataset（中文摘要生成数据集）
EDUsum是我们文章中创建中文摘要生成数据集，为了中文摘要生成任务提供数据集、基准。

```
数据量：训练集(8,000)，验证集(1,000)，测试集(1,000)
示例：
{
    title: 国外职业教育中值得借鉴的课程体系
    content: 根据理论和实践整合的程序,高职课程体系设计可采取三段型、工学交替型、实践渗透型和双元型4种模式.德国、英国、美国、加拿大以及日本等国的高职课程体系根植于不同的政治、经济和文化土壤,分别采取了不同的模式,我国大多数地区在较长时期内将继续维持以第二、三产业为主的产业结构,因此应大力借鉴德国的""双元型""模式,并同时借鉴其他国家高职教育的优点.
}
```

# 数据集划分

```
import csv
data = []
with open("教育.csv", "r", encoding='utf-8') as f:
    reader = csv.reader(f)
    for line in reader:
        a = line[0]
        b = line[1]
        data.append((a,b))
train_data = data[:8000]
valid_data = data[8000:9000]
test_data = data[9000:10000]
```

# 实验结果

|         模型          | Rouge-L | Rouge-1 | Rouge-2 | 
| :-------------------: | :------: |:---: |:---: |
|      Seq2seq      |  44.13  | 48.62 | 32.32 |
|      Albert       |  49.65  | 44.03 | 32.70 |
|     BERT-wwm      |  59.73  | 62.22 | 49.78 |
|    BERT            |  59.40  | 62.37 | 50.70 |
|  RoBERTa            |  60.26  | 63.22| 51.34 |
|  NEZHA               |  61.00  | 63.91 | 51.88 |
|  GP_Step_Sim        |  61.91  | 64.48 | 52.70 |

## Reference
如果您使用了这个数据集，请注明数据集的出处：

[1] Zhao, S., Li, Q., He, T. et al. A Step-by-Step Gradient Penalty with Similarity Calculation for Text Summary Generation. Neural Process Lett (2022). https://doi.org/10.1007/s11063-022-11031-0
