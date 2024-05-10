

Arquitetura 

<img src="Captura de tela 2024-05-09 221842.png" alt="Descrição da imagem">

Arquitetura de Clickstream da AWS

A imagem é uma arquitetura de clickstream da AWS. O clickstream é um registro das ações que um usuário realiza em um site ou aplicativo, como cliques em links, visualizações de páginas e compras. Essa arquitetura usa vários serviços da AWS para coletar, armazenar, processar e analisar dados de clickstream.

# Componentes da arquitetura

A arquitetura de clickstream da AWS é composta pelos seguintes componentes:

- **Portal da web do cliente**: Este é o ponto de partida para os usuários da sua aplicação. Quando um usuário acessa o portal da web, seus cliques e outras ações são registrados.
- **Amazon API Gateway**: Este serviço gerencia o tráfego entre o portal da web do cliente e os outros serviços da AWS.
- **AWS Lambda**: Este serviço é usado para executar funções sem servidor. Na arquitetura de clickstream, o Lambda joga os dados dos clicks do API Gateway pata kinesis data streams
- **Amazon Kinesis Data Streams**: Este serviço é usado para coletar e armazenar dados de clickstream em tempo real.
- **Amazon Kinesis Firehose**: Este serviço é usado para ingerir dados de clickstream em Kinesis Data Streams. O Firehose vai jogar os dados do Kinesis streams no S3
- **Amazon S3**: Este serviço é usado para armazenar dados de clickstream de forma duradoura. O S3 é um armazenamento de objetos escalável e durável que pode armazenar grandes volumes de dados. O firehose vai jogar em uma janela de entorno de 10 registros no tipo ode arquivo CSV, particionado dentro de folder em data : ano/mês/dia
- **Amazon Athena**: Este serviço é usado para consultar dados de clickstream armazenados no S3. O Athena é um serviço de consulta interativa que permite aos usuários consultar dados do clickstream no formato da tabela :
    - customerid
    - deviceid
    - productid
    - productcategory
    - productsubcategory
    - activitytype

- **Amazon QuickSight**: Este serviço é usado para visualizar dados de clickstream. O QuickSight é um serviço de visualização de dados que permite aos usuários criar painéis e relatórios interativos.

baseado no blog https://aws.amazon.com/blogs/industries/capture-clickstream-data-using-aws-serverless-services/
