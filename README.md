# Extração e Gerenciamento de Figuras e Tabelas de PDFs com Docling

Este projeto Python demonstra uma aplicação avançada da biblioteca `Docling` para o processamento de documentos PDF. Ele se concentra na extração granular de elementos visuais — como páginas inteiras, figuras e tabelas — de um PDF, salvando-os como imagens separadas. Além disso, o projeto mostra como exportar o conteúdo textual do PDF para formatos Markdown e HTML, com opções para incorporar ou referenciar essas imagens extraídas.

## Visão Geral

A capacidade de extrair e manipular figuras e tabelas de documentos PDF é crucial para diversas aplicações, como análise de documentos, automação de dados, criação de bases de conhecimento e machine learning. Este script realiza os seguintes passos:

1.  **Configuração de Pipeline:** Define opções específicas para o processamento de PDFs no Docling, garantindo que as imagens das páginas e dos elementos (figuras e tabelas) sejam geradas e mantidas em alta resolução.
2.  **Conversão de Documento:** Carrega um PDF (neste exemplo, um artigo do arXiv) e o converte, extraindo sua estrutura e seus elementos visuais.
3.  **Salvamento de Imagens de Páginas:** Salva cada página do PDF como um arquivo PNG individual.
4.  **Salvamento de Imagens de Figuras e Tabelas:** Itera sobre os elementos do documento, identificando figuras e tabelas e salvando suas imagens correspondentes como arquivos PNG separados.
5.  **Exportação para Markdown e HTML:** Converte o documento completo para Markdown e HTML, mostrando duas abordagens para inclusão de imagens: incorporadas diretamente no Markdown (`ImageRefMode.EMBEDDED`) e referenciadas externamente (`ImageRefMode.REFERENCED`).

## Estrutura do Projeto

* `figures.py`: O script Python principal que executa a extração e o salvamento.
* `images/`: (Diretório criado pelo script) Onde todas as imagens extraídas e os arquivos Markdown/HTML serão salvos.

## Tecnologias Utilizadas

* **Python 3**
* **`docling`**: A biblioteca principal para processamento de documentos.
    * `docling_core.types.doc`: Para tipos de elementos como `PictureItem` e `TableItem`.
    * `docling.datamodel.pipeline_options`: Para configurar o pipeline de conversão.
    * `docling.document_converter`: O conversor de documentos principal.
* **`Pillow` (PIL)**: (Implicitamente usado pelo Docling para manipulação de imagens, como `pil_image.save`) Para operações de imagem.

## Pré-requisitos

1.  **Instale a biblioteca `Docling`:** Para instalar a biblioteca `Docling`, você pode precisar de um token de acesso ou seguir as instruções de instalação específicas fornecidas pelo Docling. Geralmente, seria algo como:
    ```bash
    pip install docling
    # Ou siga as instruções no site oficial do Docling para instalação.
    ```

## Saída Esperada

Após a execução, um novo diretório `images/` será criado no mesmo local do script. Dentro dele, você encontrará:
* Arquivos PNG para cada página do PDF (ex: `2504.03277-1.png`, `2504.03277-2.png`).
* Arquivos PNG para cada figura e tabela detectada no PDF (ex: `2504.03277-table-1.png`, `2504.03277-picture-1.png`).
* Um arquivo Markdown com imagens incorporadas (ex: `2504.03277-with-images.md`).
* Um arquivo Markdown com referências externas a imagens (ex: `2504.03277-with-image-refs.md`).
* Um arquivo HTML com referências externas a imagens (ex: `2504.03277-with-image-refs.html`).

O console também exibirá uma mensagem de log indicando o tempo total de conversão.

## Configuração

* **`source`**: Altere a URL do PDF na variável `source` no arquivo `figures.py` para o documento que você deseja processar.
* **`output_dir`**: Modifique o diretório de saída se desejar que os arquivos gerados sejam salvos em outro local.
* **`IMAGE_RESOLUTION_SCALE`**: Ajuste este valor para controlar a resolução das imagens salvas. Um valor maior resultará em imagens de maior qualidade, mas também em arquivos maiores.
