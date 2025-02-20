# API Face Recognition

## Instalação

Use o [Anaconda](https://www.anaconda.com/download) para instalar o python, a versão utilizada foi 3.12.

Depois rode os comandos:
```bash
conda update --all
```
```bash
conda install -c conda-forge dlib
```

Após isso para instalar as bibliotecas utilizadas, rode o comando:
```bash
pip install -r requirements.txt

```

## Utilização

Esta Api possui 3 portas ***POST***.
 - /CadastroImagem
 - /Reconhecimento
 - /ComparaImagens

### /CadastroImagem
Armazena a imagem e as informações em uma lista para futuramente serem utilizadas pela porta **/Reconhecimento**. 

#### Entrada
```json
{
"img": "<string base64 da imagem>",
"name": "<string>",
"cpf": "<string>"
}
```
#### Saída
Se tudo der certo a mensagem de retorno será:
```json
{
"message": "Imagem cadastrada com sucesso"
}
```

### /Reconhecimento
Compara a imagem enviada com as que ja estão salvas na lista.

#### Entrada
```json
{
"img": "<string base64 da imagem>"
}
```
#### Saída
Se a imagem enviada der *match* com alguma da lista ele retornará:
```json
{
"message": "Pessoa encontrada",
"name" : "<nome da pessoa>",
"cpf": "<cpf da pessoa>",
}
```
Se não der *match*:
```json
{
"message": "Pessoa nao encontrada"
}
```
### /ComparaImagens
Verifica se é a mesma pessoa nas 2 imagens enviadas.

#### Entrada
```json
{
"img1": "<string base64 da imagem>",
"img2": "<string base64 da imagem>"
}
```
#### Saída
Se for a mesma pessoa retornará:
```json
{
"message": "Mesma pessoa"
}
```
Se não for:
```json
{
"message": "Nao e a mesma pessoa"
}
```
### Execução
Para subir a API na rede local é só rodar no terminal, na pasta do projeto, o comando:
```bash
uvicorn main:app --reload
```
