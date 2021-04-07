# tensorflowforpoets

<h1 align="center">
    <a href="https://www.java.com/pt-BR/">🔗 Python</a>
</h1>
<p align="center">🚀 Inteligência Artificial e Políticas Públicas Ambientais 🚀 </p>

<h4 align="center"> 
	🚧  Python  🚀 Em construção...  🚧
</h4>

### Features

- [x] Fatkun Batch Download da imagem
- [x] Instalar o Docker
- [x] Docker run hello-world
- [x] Clonar o repositorio do Git: tensorflow-for-poets-2
- [x] (Re) treinamento da rede
- [x] Usando o modelo retreinado


<p align="center"> :robot: Fatkun Batch Download da imagem :robot: </p>

<p align="justify"> :robot: 
Uma extensão de download de imagem útil e simples.Você pode filtrar por resolução ou link.
Apenas um clique para baixar todas as imagens selecionadas nas páginas.
Pode usar suas próprias regras para baixar a lista de imagens.
Pode mudar o nome das imagens baixada  :robot: </p>

<p align="center"> :robot: Instalar o Docker :robot: </p>

<p align="justify"> :robot: 

Docker Desktop para Windows é a versão comunitária do Docker para Microsoft Windows. 
Docker é um conjunto de produtos de plataforma como serviço que usam virtualização de nível de sistema operacional para entregar software em pacotes chamados contêineres. Os contêineres são isolados uns dos outros e agrupam seus próprios softwares, bibliotecas e arquivos de configuração.

- [ ] https://docs.docker.com/docker-for-windows/install/
- [ ] https://www.youtube.com/watch?v=W8x8Lln3i5A

:robot: </p>

<p align="center"> :robot: Clonar o repositorio do Git: tensorflow-for-poets-2 :robot: </p>

<p align="justify"> :robot: 

Antes de iniciar qualquer treinamento, você precisará de um conjunto de imagens para ensinar a modelo sobre as novas classes que deseja reconhecer. Criamos um arquivo de fotos de flores licenciadas pela Creative Commons para uso inicial. Baixe as fotos (218 MB) invocando os dois comandos a seguir:

```
docker run -it tensorflow/tensorflow:1.7.0 bash
```
```
git clone https://github.com/googlecodelabs/tensorflow-for-poets-2
```
```
cd tensorflow-for-poets-2
```

<p align="center"> :robot: Agora você deve ter uma cópia das fotos das flores. 
Confirme o conteúdo do seu diretório de trabalho emitindo o seguinte comando: :robot: </p>


 ls tf_files / flower_photos
- [ ] Você deve receber: daisy/ dandelion/ roses/ sunflowers/ tulip/ LICENSE.txt

:robot: </p>

<p align="center"> :robot: (Re) treinamento da rede :robot: </p>

<p align="justify"> :robot: 
Conforme observado na introdução, os modelos ImageNet são redes com milhões de parâmetros que podem diferenciar um grande número de classes. Estamos apenas treinando a camada final dessa rede, portanto, o treinamento terminará em um período de tempo razoável.

Comece seu retreinamento com um comando:
:robot: </p>

- [ ] Usando Mobilenet Model: São uma classe de convolução de redes neurais projetadas por pesquisadores do Google

<p align="justify"> 💻 python -m scripts.retrain  --bottleneck_dir=tf_files/bottlenecks  --how_many_training_steps 500 --model_dir=tf_files/models/mobilenet_0.50_224  --architecture=mobilenet_0.50_224  --summaries_dir=tf_files/training_summaries/mobilenet_0.50_224   --output_graph=tf_files/retrained_graph.pb --output_labels=tf_files/retrained_labels.txt --image_dir=tf_files/flower_photos/ 💻 </p>


- [ ] Usando Inception Model: É uma rede neural convolucional para auxiliar na análise de imagens e detecção de objetos , e começou como um módulo para Googlenet

```
python -m scripts.retrain  --bottleneck_dir=tf_files/bottlenecks  --how_many_training_steps 500 --model_dir=tf_files/models/inception --architecture=inception  --output_graph=tf_files/retrained_graph.pb --output_labels=tf_files/retrained_labels.txt --image_dir=tf_files/flower_photos/ 

```

<p align="center"> :robot: Usando o modelo retreinado :robot: </p>

<p align="justify"> :robot: O script de reciclagem grava dados nos dois arquivos a seguir: tf_files/retrained_graph.pb, que contém uma versão da rede selecionada com uma camada final retreinada em suas categorias. tf_files/retrained_labels.txt, que é um arquivo de texto contendo rótulos. :robot: </p>

<p align="center"> :robot: Cada execução do comando abaixo imprimirá uma lista de rótulos de flores, na maioria dos casos com a flor correta no topo (embora cada modelo retreinado possa ser ligeiramente diferente). :robot: </p>


- [ ] Se o treino foi utilizando Mobilenet Model:

```
python -m scripts.label_image --graph=tf_files/retrained_graph.pb   --image=tf_files/flower_photos/daisy/2877860110_a842f8b14a_m.jpg
    
```

- [ ] Se o treino foi utilizando Mobilenet Model:

```
python -m scripts.label_image --input_height  299  --input_width  299 --input_layer "Mul" --graph=tf_files/retrained_graph.pb  --image=tf_files/flower_photos/daisy/2877860110_a842f8b14a_m.jpg
```


