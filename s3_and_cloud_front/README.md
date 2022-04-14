# Amazon S3

O Amazon Simple Storage Service (Amazon S3) é um serviço de armazenamento de objetos **(elementos estáticos)** que oferece escalabilidade, disponibilidade de dados, segurança e performance líderes do setor. Clientes de todos os portes e setores podem armazenar e proteger qualquer quantidade de dados de praticamente qualquer caso de uso, como data lakes, aplicações nativas da nuvem e aplicações móveis. Com classes de armazenamento econômicas e recursos de gerenciamento fáceis de usar, você pode otimizar custos, organizar dados e configurar controles de acesso ajustados para atender a requisitos específicos de negócios, organizacionais e de conformidade.

### Casos de uso

#### Construir um data lake

Execute aplicações de análise de big data, inteligência artificial (IA), machine learning (ML) e computação de alta performance (HPC) para desbloquear insights de dados.

#### Faça o backup e a restauração de dados críticos
Atenda aos objetivos de tempo de recuperação (RTO), objetivos de ponto de recuperação (RPO) e requisitos de conformidade com os recursos de replicação robustos do S3.

#### Arquive dados com o menor custo
Mova os arquivos de dados para as classes de armazenamento do Amazon S3 Glacier para reduzir custos, eliminar complexidades operacionais e obter novos insights.

#### Execute aplicações nativas da nuvem
Crie aplicações nativas da nuvem rápidas e poderosas baseadas na Web que se expandem automaticamente em uma configuração altamente disponível.

___

## Conceitos
https://docs.aws.amazon.com/pt_br/AmazonS3/latest/userguide/Welcome.html

### Bucket
Um bucket é um contêiner para objetos armazenados no Amazon S3. Você pode armazenar qualquer número de objetos em um bucket.

Cada objeto está contido em um bucket. Por exemplo, se o objeto chamado photos/puppy.jpg estiver armazenado no bucket DOC-EXAMPLE-BUCKET da região oeste dos EUA (Oregon), ele poderá ser endereçado usando o URL https://DOC-EXAMPLE-BUCKET.s3.us-west-2.amazonaws.com/photos/puppy.jpg. Para obter mais informações, consulte Accessing a Bucket (Como acessar um bucket).

Ao criar um bucket, você insere um nome de bucket e escolhe a Região da AWS onde o bucket residirá. Assim que você cria um bucket, não pode mais alterar o nome do bucket ou sua região. Os nomes de bucket devem seguir as regras de nomeação de bucket. Você também pode configurar um bucket para usar o Versionamento do S3 ou outros recursos do gerenciamento de armazenamento.

Os buckets também:

- Organizam o namespace do Amazon S3 no nível mais elevado.
- Identificam a conta responsável por cobranças de transferência de dados e armazenamento.
- Fornecem opções de controle de acesso, como políticas de bucket, listas de controle de acesso (ACLs) e pontos de acesso do S3, que podem ser usados para gerenciar o acesso aos recursos do Amazon S3.
- Serve como a unidade de agregação para relatório de uso.

### Objects
Os objetos são as entidades fundamentais armazenadas no Amazon S3. Os objetos consistem em metadados e dados de objeto. Os metadados são um conjunto de pares de nome e valor que descrevem o objeto. Esses pares incluem alguns metadados padrão, como a data da última modificação, e metadados HTTP padrão, como o Content-Type. Você também pode especificar metadados personalizados no momento em que o objeto é armazenado.

### Keys
Uma chave de objeto (ou nome da chave) é um identificador exclusivo de um objeto em um bucket. Cada objeto em um bucket tem exatamente uma chave. A combinação de um bucket, chave de objeto e, opcionalmente, o ID de versão (se o Versionamento do S3 estiver habilitado para o bucket) identifica exclusivamente cada objeto. Portanto, é possível pensar no Amazon S3 como um mapa de dados básico entre "bucket + chave + versão" e o objeto em si.

Cada objeto no Amazon S3 pode ser endereçado exclusivamente por meio da combinação do endpoint de serviço da web, do nome de bucket, da chave e, opcionalmente, de uma versão. Por exemplo, no URL https://DOC-EXAMPLE-BUCKET.s3.us-west-2.amazonaws.com/photos/puppy.jpg, DOC-EXAMPLE-BUCKET é o nome do bucket e /photos/puppy.jpg é a chave.

Um objeto é identificado exclusivamente em um bucket por uma chave (nome) e um ID da versão (se o Versionamento do S3 estiver habilitado no bucket). Para obter mais informações sobre objetos, consulte [Visão geral de objetos Amazon S3.](https://docs.aws.amazon.com/pt_br/AmazonS3/latest/userguide/UsingObjects.html)

### Regions
Você pode escolher a região da Região da AWS geográfica onde o Amazon S3 armazena os buckets criados. É possível escolher uma Região para otimizar a latência, minimizar os custos ou atender a requisitos regulatórios. Os objetos armazenados em uma Região da AWS nunca saem dela, a não ser que você os transfira ou os replique explicitamente para outra região. Por exemplo, os objetos armazenados na região da UE (Irlanda) nunca saem dela.

### Data Consistency

___

## CLI

``` bash
>> aws configure
AWS Access Key ID [None]: ***
AWS Secret Access Key [None]: ***
Default region name [None]: us-east-1
Default output format [None]: json
```

Criar Bucket
``` bash
aws s3 mb s3://bucket-create-by-cli
```

Upload 
``` bash
aws s3 cp aws-cli-user s3://bucket-create-by-cli
```

Download 
``` bash
aws s3 cp s3://bucket-create-by-cli/aws-cli-user ./downloads
```

Remove 
``` bash
aws s3 rm s3://bucket-create-by-cli/aws-cli-user
```

Sync -> sincronizar diretorios 
``` bash
aws s3 sync downloads/ s3://bucket-create-by-cli
```
___
## Hospedagem de Site Estático

___

# Amazon CloudFront

**O Cliente não acessa diretamente o S3, ele passa pelo CloudFront, que mantem a informção em cache. Gerando economia.**

Entregue conteúdo com segurança com baixa latência e altas velocidades de transferência

- Reduza a latência entregando dados através de mais de 310 pontos de presença (POPs) dispersos globalmente com mapeamento de rede automatizado e roteamento inteligente.
- Melhore a segurança com criptografia de tráfego e controles de acesso e use o AWS Shield Standard para se defender contra ataques de DDoS sem custo adicional.
- Reduza custos com solicitações consolidadas, opções de definição de preço personalizáveis e taxas zero para transferência de dados de origens da AWS.
- Personalize o código que você executa na borda da rede de entrega de conteúdo (CDN) da AWS usando recursos de computação sem servidor para equilibrar custo, performance e segurança.

### Casos de uso

#### Forneça sites rápidos e seguros
Alcance visualizadores em todo o mundo em milissegundos com compactação de dados integrada, recursos de computação de borda e criptografia em nível de campo.

#### Acelere a entrega de conteúdo dinâmico e as APIs
Otimize a entrega dinâmica de conteúdo da Web com a infraestrutura de rede global da AWS desenvolvida para fins específicos e rica em recursos que oferece suporte à terminação de borda e WebSockets.

#### Transmita vídeos ao vivo e sob demanda
Inicie streams rapidamente, reproduza-os com consistência e entregue vídeo de alta qualidade para qualquer dispositivo com a integração do AWS Media Service e do AWS Elemental.
 
#### Distribua patches e atualizações
Dimensione automaticamente para fornecer software, patches de jogos e atualizações de IoT over-the-air (OTA) em grande escala com altas taxas de transferência.