# AI Agent

Agente de IA para linha de comando (CLI), escrito em Python. Ele recebe uma tarefa em linguagem natural, escolhe entre um conjunto de funções pré-definidas e repete esse ciclo até concluir a tarefa.

## O que o agente faz

1. Recebe uma tarefa escrita pelo usuário.
2. Escolhe entre as funções disponíveis para trabalhar nela:
   - listar arquivos e diretórios
   - ler o conteúdo de um arquivo
   - criar ou sobrescrever um arquivo
   - executar um arquivo Python
3. Repete o passo 2 até terminar a tarefa. Se não chegar a uma resposta final em 20 iterações, o programa encerra com erro.

Para se comunicar com o modelo, o projeto usa o SDK oficial da OpenAI apontando para a [OpenRouter](https://openrouter.ai/), com o modelo de roteamento gratuito `openrouter/free`, que escolhe automaticamente um modelo gratuito disponível a cada requisição.

## Pré-requisitos

- [Git](https://git-scm.com/)
- [uv](https://docs.astral.sh/uv/getting-started/installation/): gerenciador de pacotes e ambientes Python. Ele cria o ambiente virtual, instala as dependências nas versões exatas registradas no `uv.lock` e usa a versão de Python do projeto.

## Instalação

Clone o repositório e instale as dependências:

```bash
git clone https://github.com/joaoguilherme-jg/ai-agent.git
cd ai-agent
uv sync
```

O `uv sync` cria a pasta `.venv` e instala tudo que o projeto precisa.

## Configuração da chave de API

Copie o arquivo de exemplo:

```bash
cp .env.example .env
```

```
OPENROUTER_API_KEY=sua-chave-aqui
```

(cuidado para não commitar o .env e sua chave junto.)

## Uso

Passe a tarefa como argumento:

```bash
uv run main.py "Liste os arquivos disponíveis e explique o que cada um faz"
```

O `uv run` executa o programa dentro do ambiente virtual do projeto, sem precisar ativá-lo manualmente.

Para ver também o uso de tokens e os resultados das funções chamadas, adicione `--verbose`:

```bash
uv run main.py "Liste os arquivos disponíveis e explique o que cada um faz" --verbose
```

## Aviso

Este é um projeto de estudo. O agente pode criar e modificar arquivos e executar código Python, então use apenas em ambiente de teste e revise com cuidado o que ele fizer.

## Créditos

Desenvolvido a partir do curso de criação de agentes de IA do [Boot.dev](https://www.boot.dev/).
