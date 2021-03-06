# Знакомство с библиотеками Horovod и Pytorch.distributed

В данном примере показано, как можно писать скрипты для распределенного обучения `Pytorch` модели с использованием одной из двух библиотек:
 * [Horovod](https://github.com/horovod/horovod)
 * [Pytorch.distributed](https://pytorch.org/tutorials/intermediate/dist_tuto.html)

Обратите внимание на параметр запуска `type` в `client_lib.Job` и его возможные значения:
 * `type="horovod"` для запуска обучения с использованием библиотеки `Horovod`.
 * `type="pytorch"` для запуска обучения с использованием `DistributedDataParallel` и `Pytorch`.

Для запуска примера загрузите в веб-интерфейс [Jupyter Server внутри AI Cloud](https://aicloud.sbercloud.ru/_/jupyter/) следующие файлы:

 * [pytorch_example.ipynb](pytorch_example.ipynb) (отправка задач на кластер "Кристофари")
 * [train_distributed_example.py](train_distributed_example.py) (распределенное обучение с использованием `DistributedDataParallel` из библиотеки `Pytorch.distributed`)
 * [train_horovod_example.py](train_horovod_example.py) (распределенное обучение с использованием бибилотеки `Horovod`)
 
 
 Для запуска и отладки скриптов из-под Jupyter Notebook:
 
 Выберите один из образов с пометкой *horovod* (прим. jupyter-horovod-tf15)
 
 Запуск с Horovod:
 ```
 mpirun -np {GPU count} python train_horovod_example.py
 ```
 Запуск с Pytorch.distributed:
 ```
 python -m torch.distributed.launch --nproc_per_node {GPU count} train_distributed_example.py
```
