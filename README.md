# Sistema de Analise de Detecção de Quedas - TCC

Um sistema baseado em visão computacional para uma Prova de Conceito para o Trabalho de Conclusão do Curso, do Curso Superior de Tecnologia em Gestão de Dados - CSTGD, do Centro de Educação Aberta e a Distancia - CEAD, da Universidade Federal do Piauí - UFPI

Esse sistema usa o modelo YOLOv11 da Ultralytics para fazer analise de vídeos onde ocorrem situações de risco, como quedas e proximidade.

Ele é composto por um arquivo base que foi a primeira idealização do projeto no qual era usado no Google Colab para execução que posteriormente foi passado para desenvolvimento local para menor gargalo de performance. Onde foi criado os modelos "Sem Velocidade" e o "Com Velocidade" que possui uma trava de segurança para servir de prova no artigo escrito.

Para executar o código é preciso baixar a biblioteca da Ultralytics:

```
pip install ultralytics openCV-python numpy
```

E para execução em lote com vários vídeos use o código abaixo:

```
$modelos = @(
    "modelos\yolo11n.pt",
    "modelos\yolo11s.pt",
    "modelos\yolo11m.pt",
    "modelos\yolo11l.pt",
    "modelos\yolo11x.pt"
)

$videos = Get-ChildItem "videos\*.mp4"

foreach ($video in $videos) {
    Write-Host "Iniciando análise do vídeo: $($video.FullName)" -ForegroundColor Green

    foreach ($modelo in $modelos) {
        python main.py --SOURCE $video.FullName --MODEL $modelo
    }
}
```

Ps. Lembre-se colocar os vídeos na pasta de vídeos, já as pastas de relatórios e modelos o próprio código cria.
