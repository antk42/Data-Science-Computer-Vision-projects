
<p align="center"><b>Generative adversarial networks. PyTorch</b></h3>
<p align="center"><img src="https://i.ibb.co/n10yT0q/705c61ceda92e3cb04476986cc6f11e9.jpg" alt="705c61ceda92e3cb04476986cc6f11e9" border="0"></p>





## Контекст


В системе GAN одна из сетей (сеть G, от Generator) генерирует образцы ， а другая (сеть D, от Discriminator) старается отличить правильные («подлинные») образцы от неправильных. Используя набор переменных латентного пространства, генеративная сеть пытается слепить новый образец, смешав несколько исходных образцов. Дискриминативная сеть обучается различать подлинные и поддельные образцы, а результаты различения подаются на вход генеративной сети так, чтобы она смогла подобрать лучший набор латентных параметров, и дискриминативная сеть уже не смогла бы отличить подлинные образцы от поддельных. Таким образом целью сети G является повысить процент ошибок сети D, а целью сети D является наоборот улучшение точности распознавания.

Дискриминационная сеть D, анализируя образцы из оригинальных данных и из подделанных генератором, достигает некоторой точности различения. Генератор при этом начинает со случайных комбинаций параметров латентного пространства , а после оценки полученных образцов сетью D, применяется метод обратного распространения ошибки, который позволяет улучшить качество генерации, подправив входной набор латентных параметров. Постепенно искусственные изображения на выходе генеративной сети становятся всё более качественными. Сеть D реализуется как свёрточная нейронная сеть, в то время как сеть G наоборот разворачивает изображение на базе скрытых параметров.

В процессе совместного конкурентного обучения, если система достаточно сбалансирована, достигается минимаксное состояние равновесия, в котором обе сети значительно улучшили своё качество, и теперь сгенерированные изображения могут быть использованы практически как настоящие.

Идея состязательного обучения была выдвинута в 2013 году Li, Gauci и Gross. Этот метод называется также «обучением Тьюринга», так как ставит целью пройти тест Тьюринга. [источник](https://ru.wikipedia.org/wiki/%D0%93%D0%B5%D0%BD%D0%B5%D1%80%D0%B0%D1%82%D0%B8%D0%B2%D0%BD%D0%BE-%D1%81%D0%BE%D1%81%D1%82%D1%8F%D0%B7%D0%B0%D1%82%D0%B5%D0%BB%D1%8C%D0%BD%D0%B0%D1%8F_%D1%81%D0%B5%D1%82%D1%8C)

Нам предстоит обучить и протестировать собственный `GAN`. Обучим `GAN` генерировать лица людей и посмотрим на то, как можно оценивать качество генерации


Примеры изображений:

<img src="https://i.ibb.co/jzGpJLG/001.png" alt="001" border="0">
<img src="https://i.ibb.co/YW5179t/002.png" alt="002" border="0">
<img src="https://i.ibb.co/cCJ7nRD/003.png" alt="003" border="0">