# Documentação.


## Ativar virtualenv
```
    pip install virtualenv
```
- Linux/WSL
```
    #virtualenv  <nomeDaVM>
    virtualenv venv
```
```
    source venv/bin/activate #para ativar venv
    deactivate #para desativar
```

## Requirements.txt
```
    pip install -r requirements.txt
```
- Flask == 3.0.3
- marshmallow == 3.23.1


## ENDPOINTS

### 1. POST /aluno
Adiciona um novo aluno
- carrega os dados recebidos da request HTTP(recurso: .json) e converte os dados em uma instacia de classe de acordo com o schema fornecido

> request_data = request.json

```
{
    "idade": 28,
    "disciplina": "Programação para a Web II"
}
````

> .load(request_data)

```
    # AlunoSchema(28, "Programação para a Web II")
```

 converte os dados do schema em uma string JSON e então cadastra o novo aluno
> dupms(result)
```
    dumps(alunoSchema) # '{"idade": 28, "disciplina": "Programação para a Web II"}'
```
> def cadastrarAluno(json_str: str):

recebe uma string JSON, converte para um formato Python e adiciona na lista `alunos = []`

> ValidationError

Utiliza o método da biblioteca marshmallow para validar as informações cadastradas e lançar exceção caso ocorra
- Uma exceção ocorre quando os dados para o schema não cumprem os requisitos definidos em seus campos
-- campos ausentes
-- valores incompatíveis
A validação é feita de modo automático (pela própria biblioteca) ou personalizada (escrevendo suas próprias validações)

### 2. POST /relatorio
Adiciona um novo relatório
- segue o mesmo padrão de cadastro de aluno
> 1. receber request
> 2. carregar schema
> 3. converter dados
> 4. ativar método de cadastro
> 5. validar campos

## Persistencia dos dados
`alunos = []`

`relatorio = []`

- persistidos localmente durante execução do código e perdidos após finalização
- Pode se utilizar bibliotecas de bancos de dados (ex: SQLite, Postgres, MongoDB, etc) para persistir os dados e salvar em arquivos


