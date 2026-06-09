# Mini mundo gerador de OS simples

## Entidades
- Status: que classifica o estado da OS e traça uma linha do tempo do andamento.

- Prestador: dados do prestador de serviço, Nome do resposavel, endereço, contato(Email, telefone, instagram, facebook entre outros).

- Cliente: quem recebe o serviço sendo empresa ou pessoa física, contendo dados como, nome completo, CPF ou CNPJ, contatos(telefone,email).

- Dados do equipamento: Tipo(Desktop,Notebook,All-in-One,Outro),Marca, Modelo, Numero de série, Sistema operacional, iten deixado com o notebook, senha de acesso.

- Descrição do problema pelo cliente, uma descrição do cliente do problema que está ocorrendo.

- Diagnostico técnico, uma descrição realizada pelo técnico sobre qual o problema.

- Serviços a serem executados, podem ser N serviços que podem ser executados na OS.

- Itens usado: é composto pelo item, a descrição a quantidade valor da unidade e valor total dos itens.

- Pagamento: como vai ser realizado a forma de pagamento.

- Observaçoes de termos de serviço, são campos que tem pontos a serem visados pelo prestador e o tomador no para prestação de serviço.

# Entidades que podem escalar

- Items, Status, Serviços.

## modelagem simples mermaid

```mermaid
erDiagram

    tp_item{
        String nome
        String descricao
        String valor_un
    }

    tp_serviço{
        String nome
        String descricao
        String valor
    }

    tp_status{
        String nome
        String descricao
    }

    prestador{
        string nome
        string contatos
        string rua
        string bairro
        string cep
        string estado
        string numero
        string cidade
    }

    rl_pagamento_nota{
        date realizado
    }

    rl_item{
        double valor_total
    }

    contatos{
        Enum[TelefoneEmailInstagramEtc] tipo
        string valor
    }

    nota_serviço{
        String descricao_cliente
        String descricao_tecnica
    }

    tp_pagamento{
        string tipo 
    }

    prestador ||--|{ contatos : Contem
    nota_serviço ||--|| prestador : Realizado
    nota_serviço ||--|{ tp_status : define
    nota_serviço ||--|{ rl_pagamento_nota : pago
    nota_serviço ||--|{ tp_serviço : defini 
    nota_serviço ||--|{ rl_item : contem
    tp_item }|--|{ rl_item : contem
    tp_pagamento ||--|| rl_pagamento_nota : defini

```"# OS_manager" 
