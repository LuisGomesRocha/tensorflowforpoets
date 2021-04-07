# tensorflowforpoets

<h1 align="center">
    <a href="https://www.java.com/pt-BR/">🔗 Python</a>
</h1>
<p align="center">🚀 Inteligência Artificial e Políticas Públicas Ambientais 🚀 </p>

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

Abrir seu cmd : Pressione Win+X para abrir o menu contextual e clique na opção Prompt de Comando ou Prompt de Comando (Admin).

</p>

```
docker pull tensorflow / tensorflow: 1.7.0
```
```
docker run -it tensorflow/tensorflow:1.7.0 bash
```
Seu prompt deve ser "root @ xxxxxxx: / notebooks/tensorflow-for-poets-2" 
```
apt-get update
```
```
apt-get install git
```

```
git clone https://github.com/googlecodelabs/tensorflow-for-poets-2
```

```
cd tensorflow-for-poets-2
```

```
curl http://download.tensorflow.org/example_images/flower_photos.tgz \
    | tar xz -C tf_files
```

<p align="center"> :robot: Agora você deve ter uma cópia das fotos das flores. 
Confirme o conteúdo do seu diretório de trabalho emitindo o seguinte comando: :robot: </p>

```
cd tf_files
```

```
cd flower_photos
```

```
dir
```
- [ ] Você deve receber: daisy/ dandelion/ roses/ sunflowers/ tulip/ LICENSE.txt

Agora precisamos voltar para pasta "root @ xxxxxxx: / notebooks/tensorflow-for-poets-2" , então suba dois níveis digitando:

```
cd ..
```

```
cd ..
```

<p align="center"> :robot: (Re) treinamento da rede :robot: </p>

<p align="justify"> :robot: 
Conforme observado na introdução, os modelos ImageNet são redes com milhões de parâmetros que podem diferenciar um grande número de classes. Estamos apenas treinando a camada final dessa rede, portanto, o treinamento terminará em um período de tempo razoável.

Comece seu retreinamento com um comando:
:robot: </p>

- [ ] Usando Mobilenet Model: São uma classe de convolução de redes neurais projetadas por pesquisadores do Google

```
python -m scripts.retrain  --bottleneck_dir=tf_files/bottlenecks  --how_many_training_steps 500 --model_dir=tf_files/models/mobilenet_0.50_224  --architecture=mobilenet_0.50_224  --summaries_dir=tf_files/training_summaries/mobilenet_0.50_224   --output_graph=tf_files/retrained_graph.pb --output_labels=tf_files/retrained_labels.txt --image_dir=tf_files/flower_photos/
```

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


<h4 align="center"> 
	🚧  Python  🚀 Em construção...  🚧
</h4>

<p align="center"> :robot: Agora podemos (Re)treinar nossa rede com imagens que achamos interessantes classificar...:robot: </p>

<p align="center"> :robot: Utilizando a extenção do Chrome Fatkun, busquei por fotos com “Ferrugem” (Puccinia sp ) e “Oidio” (Erysiphe difusa) nas folhas... perceba que nesse primeiro momento apenas busquei por imagem com a finalidade de montar um DataSet para treinar a rede neural... 9 IMPORTANTE que seu banco de imagens para serem analisadas sejam verificadas evitando divergência no treinamento).:robot: </p>
 
<p align="center"> :robot: Salvei as fotos em duas pastas com seus respectivos nomes, e coloquei essas duas pastas com as fotos dentro de outra com o nome “Apresentacao”, e por fim compactei utilizando zip. Criei em seguida outra pasta com três fotos de exemplos de Ferrugem e Oídio, renomeadas como Teste 1, Teste n, Teste 6. Após o treinamento da nossa rede, utilizaremos essas fotos para verificar se o modelo está acertando...:robot: </p>

<p align="center"> :robot: Esses arquivos ficaram no Desktop do meu pc, e possuem os seguintes nomes e caminhos: robot: </p>

Nome|  Path (Caminho)  
-----------  | -----------------------------------      
Apresentacao.zip| C:\Users\luisa\Desktop\Apresentacao.zip
Teste.zip| C:\Users\luisa\Desktop\Teste.zip

<p align="center"> :robot:  Agora, abrindo um outro Command Prompt, digitamos o comando abaixo que irá nos fornecer o nome do container ou ID curto do container:: :robot: </p>

```
docker ps
```

CONTAINER ID |            IMAGE            | COMMAND | CREATED | STATUS |  PORTS  |         NAMES
-----------  | --------------------------- | ------  |  ----   |  ----  | ------  | --------------------
f917e44bf1fb | tensorflow/tensorflow:1.7.0 | "bash"  |  ...    |  ...   |6006/tcp | intelligent_heyrovsky


<p align="center"> :robot:  Vamos precisar agora do ID completo do container preenchendo “SHORT_CONTAINER_ID “ no código abaixo :  :robot: </p>

```
docker inspect -f   '{{.Id}}'  SHORT_CONTAINER_ID-or-CONTAINER_NAME

ou seja no nosso caso …

docker inspect -f   '{{.Id}}'  f917e44bf1fb

```

Vamos receber:
```
'f917e44bf1fbe0cec3f44282d78af4db3cd65335d6d12df19302d26215517623'
```

```
sudo cp path-file-host /var/lib/docker/aufs/mnt/FULL_CONTAINER_ID/PATH-NEW-FILE

ou seja no nosso caso …

sudo cp C:\Users\luisa\Desktop\Apresentacao.zip /var/lib/docker/aufs/mnt/** f917e44bf1fbe0cec3f44282d78af4db3cd65335d6d12df19302d26215517623**/root/file.txt
```

